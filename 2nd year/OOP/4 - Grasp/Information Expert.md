
## Пример несоблюдения

```C# 
public record OrderItem(
	int Id,
	decimal Price,
	int Quantity);

public class Order
{
	private readonly List<OrderItem> _items;

	public Order()
	{
		_items = new List<OrderItem>();
	}
	
	public IReadOnlyCollection<OrderItem> Items -> _items;
}

public record Receipt(
	decimal TotalCost,
	DateTime Timestamp);

public class ReceiptServis
{
	public Receipt CalculateReceipt(Order customer)
	{
		var totalCost = customer.Items.Sum(order -> order.Price * order.Quantity);
		
		var timestamp = DateTime.Now;

		return new Receipt(totalCost, timestamp);
	}
}
```

## Почему это плохо

1. Нарушение [[Single Responsibility Principle (SRP)]].
2. Проблемы с пере использованием либо копипаста, либо нелогичная связь между модулями.
3. Усложнённое тестирование.

## Пример соблюдения

```C#
public record OrderItem(
	int Id,
	decimal Price,
	int Quantity);
{
		public decimal Cost -> Price * Quantity;
}

public class Order
{
	private readonly List<OrderItem> _items;

	public Order()
	{
		_items = new List<OrderItem>();
	}
	
	public IReadOnlyCollection<OrderItem> Items -> _items;

	public decimal TotalCost -> _items.Sum(x -> x.Cost);
}

public record Receipt(
	decimal TotalCost,
	DateTime Timestamp);

public class ReceiptServis
{
	public Receipt CalculateReceipt(Order customer)
	{
		var totalCost = customer.TotalCost;
		
		var timestamp = DateTime.Now;

		return new Receipt(totalCost, timestamp);
	}
}
```

## Дополнительная информация

Информация должна обрабатываться там, где она храниться.