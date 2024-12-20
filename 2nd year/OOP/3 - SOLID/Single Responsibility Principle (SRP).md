#### Определение
Проектирование типов таким образом, что они имеют единственную причину для изменения.

#### Пример несоблюдения

```C#
public record OperationResult(...);

public class ReportGenerator
{
	public void GenerateExcelReport(OperationResult result)
	{
		...
	}
	
	public void GeneratePdfReport(OperationResult result)
	{
		...
	}
}
```

#### Пример соблюдения

```C#
public record OperationResult(...);

public interface IReportGenerator
{
	void GenerateReport(OperationResult result);
}

public class ExcelReportGenerator : IReportGenerator
{
	public void GenerateReport(OperationResult result)
	{
		...
	}
}

public class PdfReportGenerator : IReportGenerator
{
	public void GeerateReport(OperationResult result)
	{
		...
	}
}
```

