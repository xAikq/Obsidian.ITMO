## **Анекдоты:**

- Sex - это "пол" с английского, если что.
- Мы изобрели фреймворк. Вау, нифига себе.
- Шарписты и джависты согласны только в том, что у них всё украл Kotlin.
- А когда у нас Spring будет? Примерно через 3-4 недели.
- Вспоминаем, да? НА ОПТИМИЗАЦИЮ В JAVA ВСЕМ НАСРАААТЬ.
- Тебе прям неинтересно, ты джавист? Сосал?
- Погода ГОВНА КУСОК, твою мать, хочу СОЛНЦЕ!
- Ну твою мать! Всё, у нас ЖОПА (получили exception).
- Я почистила память, ура, упадём через 5 минут.
- Я щас кидаться в тебя начну.
- Ой ну докопался, a? Ну ошибся, я тоже человек, ещё и плохой программист.
- Писать круто, красиво и прикольно, но красивее и прикольнее вам скажет любой разработчик на Kotlin'e.

---
## **Классы, методы, переменные, пакеты**

```java
pachage start;

public class AnyName{
	
	private int age;
	
	public int sum(int a, int b){
		return a+b;
	}
	
	public static void main(String[] args){
	}
}
```

`pachage (java)` = `namespace (C#)`

`import (java)` = `using (C#)`

---
## **Collections framework**

![[Pasted image 20250217185933.png]]

В Java `I` в начале интерфейса не пишется.

### **Generic**

**Generic** - шаблон в Java

```Java
List<string> list = new ArrayList<>()

list.add("string")

list.add(5) (мы так не умеем :с)
```

---
## **Map**

```Java
Map<key, value> map;

map.put(1, "one")
```

---
## **Абстрактные классы, интерфейсы, перечисления**

```Java
// Наследование: (Класс)
public class Dog extends Animal {
	// код класса
}

// Имплементация: (Интерфейс)
public class Cat implements Eatable{
	// код класса
}
```

---
## **Исключения**

![[Pasted image 20250217191724.png]]

`Error` = ГГ.

`Exception` = Анлак.

```Java
Exception

string message;
Exception e;
```

---
## **Обработка Exception**

`RunTime` - необрабатываемые Exceptions

`Exception` - Обрабатываемый Exception (наследники базового Exception'a)

```Java
public Integer doSmth(String[] args) {
	throw new Exception("AAA!!1!")
	// Мы идём лесом
}

public Integer doSmth1(String[] args) throws Exception {
	throw new Exception("AAA!!1!")
	// Мы указали, что будем кидать Exception, так что всё гуд.
}

public Integer doSmth2(String[] args) {
	doSmth1(args);
	// Тоже идём лесом (без try/catch)
}

public Integer doSmth3(String[] args) {
	try {
		doSmth1(args);
	} catch Exception {
		System.outintln("e.message")
	}
	// Вот теперь всё тип-топ.
}
```

---
## **IOException**

Можно объединить одним словом `Exception`, но лучше не стоит...

но лучше `Exception | IOException`

```Java
public Integer doSmth4(String[] args) {
	try {
		doSmth1(args);
	} catch IOException {
		// пум пум пум
	} catch Exception {
		System.outintln("e.message")
	} finally {
		// закрыли соединение с файлми;
	}
```

Можно ещё вот так:

```Java
try (...) {
	// что-то
} catch Exception {
	// что-то
}
```

Это вместо `finally` 