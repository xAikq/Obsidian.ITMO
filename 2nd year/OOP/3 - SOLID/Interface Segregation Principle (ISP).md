## Определение

Проектирование маленьких абстракций, которое ответственны за свой конкретный функционал, а не одной всеобъемлющей, содержащий много различного.
## Пример несоблюдения

```C#
public interface ICanAllDevice
{
	void Print();
	
	void PlayMusic();
	
	void BakeBread();
}
```

## Почему это плохо

Абстракции обрастают лишними, не нужными для всех её пользователей поведениями. Это приводит к большому пространству для ошибок.

ISP - это по факту [[Single Responsibility Principle (SRP)]] для интерфейсов, нарушение которого приводит к нарушению [[Single Responsibility Principle (SRP)]] у реализации.

#### Пример соблюдения

```C#
public interface IPrinter
{
	Void Print();
}

public interface IMusicPlayer
{
	void Play();
}

public interface IBakery
{
	void BakeBread();
}
```


