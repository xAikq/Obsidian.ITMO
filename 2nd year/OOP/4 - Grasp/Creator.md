

# Creator


## Пример несоблюдения

```C#
public class Order
{
	private readonly List<OrderItem> _items;

	...

	public Order AddItem(OrderItem item)
	{
		_items.Add(item);
		return this;
	}
}

public class OrderService
{
	public Order CreateDefaultOrder()
	{
	var order = mew Order()
		.AddItem(new OrderItem(1, 100, 1))
		.AddItem(new OrderItem(2, 1000, 3));

	return order;
	}

}
```

## Пример соблюдения

```C#
public class Order
{
	private readonly List<OrderItem> _items;

	public Order AddItem(
		int id,
		decimal price,
		int quantity)
	{
		_items.Add(new OrderItem(id, price, quantity));
		return this;
	}
}

public class OrderService
{
	public Order CreateDefaultOrder()
	{
	var order = mew Order()
		.AddItem(1, 100, 1)
		.AddItem(2, 1000, 3);

	return order;
	}
}
```

## Дополнительная информация

Ответственность за создание используемых объектов должна лежать на типах, их использующих

## Подводные камни

1. Добавляется неявная связность между конструктором модели и методом создателя
2. Необходимость обладать всеми данными для создания может привести к нарушению [[Single Responsibility Principle (SRP)]] создателем.
3. Пере сборка объектов может ухудшить производительность.

```C#
public class OrderService
{
	public Order CreateDefaultOrder(
		IEnumerable<OrderItem> Items)
	{
		var order = new Order()
			.AddItem(1, 100, 1)
			.AddItem(2, 1000, 3);

		foreach (var item in items)
		{
			order.AddItem(
				item.Id,
				item.Price,
				item.Quantity);
		}
	
		return order;
	}
}
```
