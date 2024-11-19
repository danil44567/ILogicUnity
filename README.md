# Памятка по Unity C#
***
## Переменные
Для объявления переменных используется следующий синтаксис:

**[Атрибут] МодификаторДоступа Тип Название**

<details><summary>Атрибут</summary>

----
Является не обязательным для указания, а нужен, чтобы добавить переменной какие-то свойства

Указывается внутри [ ]

Например атрибут позволяющий  сделать переменную видимой в ``инспекторе``:
```
[SerializeField]
```

----
</details>

<details><summary>Модификаторы доступа</summary>
	
----
Используется для обозначения доступности переменной из других классов (скриптов)

На данный момент используем два основных модификатора доступа

Модификатор, указывающий на то, что к нашей переменной могут обращаться извне, а также позволяющий видеть нашу переменную в окне инспектора:
```
public
```

Модификатор, скрывающий переменную от остальных классов:
```
private
```
Модификатор доступа не является обязательным атрибутом, если его не указать то будет использован модификатор ``private``

----
</details>

<details><summary>Тип</summary>

----
Указывает на тип переменной, это может быть любой доступный тип

Например, типы из C#:

* ``int`` — целое число
* ``float`` — число с плавающей точкой
* ``string`` — строка
* ``bool`` — булевое значение

Также в качестве типа может быть указано название вашего класса (скрипта)

----
</details>

<details><summary>Название</summary>

----
Используется при обращении к объявленной переменной в скрипте

Правила:
* Не может начинаться с цифры:
	* :x: `0count`
	* :x: `1234`
	* :x: `45red`
	* :heavy_check_mark: `variable5`
* Не может быть пробелов:
	* :x: `space name`
	* :heavy_check_mark: `notSpaceName`
* Не может совпадать с ключевыми словами языка
	* :x: `void`
	* :x: `if`
	* :heavy_check_mark: `ifYou`

----
</details>

#### Примеры

Целочисленная переменная с именем `count` доступная другим классам и отображаемая в инспекторе:
```
public int count;
```
Переменная с числом с плавающей точкой с именем `speed`, доступная другим классам и отображаемая в инспекторе:
```
public float speed;
```

Переменная, ссылающаяся на объект сцены `GameObject`, не доступная другим классам, но отображаемая в инспекторе:
```
[SerializeField] private GameObject target;
```

Логическая переменная, не доступная другим классам и не отображаемая в инспекторе:
```
private bool isCheck;
```

## Методы
Синтаксис написания метода: **МодификаторДоступа ВозвращаемыйТип Название (Аргумент)**

`void` — это специальный тип методов, который говорит, что метод ничего не возвращает 
```
public void FunctionName() 
{
	// Код выполняемый функцией
}
```

<details><summary>Создание локальной перемменной в методе</summary>

----
Локальной переменная - это переменная, которая существует внутри метода.

Она используются для хранения временных данных, которые не нужны вне этого метода. Создаются при объявлении в методе и уничтожаются при выходе из него.

**Пример**

```
public class ClassName: MonoBehaviour
{
	public void FunctionName() 
	{
		int id = 1 + 5; 
		Debug.Log(id);
	}

	private void Start()
	{
		FunctionName();
	}
}
```

----

</details>

<details><summary>Модификаторы доступа</summary>

----

`public` - доступен из любого внешнего скрипта

**Пример**
```
// ClassA.cs
public class ClassA : MonoBehaviour
{
	public void PublicMethod() 
	{
		int id = 1; 
		Debug.Log(id);
	}
}

// ClassB.cs
public class ClassB: MonoBehaviour
{
	[SerializeField] private ClassA classA; //Привязываем код в инспекторе
	private void Start
	{
		classA.PublicMethod(); //Вызов метода из скрипта ClassA
	}
}
```
`private`- доступен только внутри класса

**Пример**
```
public class ClassName : MonoBehaviour
{
	private void FunctionName() 
	{
		int id = 1;
		Debug.Log(id);
	}

	private void Start()
	{
		FunctionName(); //Вызов метода
	}
}
```
<details><summary>Дополнительно</summary>
	
`protected` - доступен только классам-наследникам

**Пример**
```
public class ClassParent: MonoBehaviour // Родитель
{
	protected void FunctionName() 
	{
		int id = 1;
		Debug.Log(id);
	}

}

public class ClassChild: ClassParent // Наследник
{
	private void Start()
	{
		FunctionName();
	}

}
```
</details>

----
</details>

<details><summary>Название</summary>

----
Используется при обращении к объявленном методе в скрипте

Правила:
* Не может начинаться с цифры:
	* :x: `0count`
	* :x: `1234`
	* :x: `45red`
	* :heavy_check_mark: `variable5`
* Не может быть пробелов:
	* :x: `space name`
	* :heavy_check_mark: `notSpaceName`
* Не может совпадать с ключевыми словами языка
	* :x: `void`
	* :x: `if`
	* :heavy_check_mark: `ifYou`

----
</details>

<details><summary>Аргумент</summary>

----

Являеться не обязательным. Нужен для передачи данных в метод.

В методе может быть несколько аргументов

<details><summary>Пример</summary>
	
```
// ClassName.cs
public class ClassName : MonoBehaviour
{
    public void ShowMessage(string message, int number)
    {
        Debug.Log(message + " " + number);
    }

    private void Start()
    {
        ShowMessage("Привет", 42); // Вывод: "Привет 42"
    }
}
```
</details>
	
В качестве типо можно использова любой существующий тип 

Например, типы из ``C#``:
* ``int`` — целое число
* ``float`` — число с плавающей точкой
* ``string`` — строка
* ``bool`` — булевое значение

Например, типы из ``Unity``:
* ``Vector3`` — Положение в пространстве
* ``Transfrom`` — Ссылка на компонент ``Transform`` у объекта
* ``GameObject `` — Ссылка на объект в Unity

<details><summary>Примеры вызовов методов с аргументами</summary>

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(int message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage(7);
    }
}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(float message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage(7.5f);
    }
}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(string message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage("Hello!");
    }
}

```

```
public class ClassName : MonoBehaviour
{
    public void ShowMessage(bool message)
    {
        Debug.Log(message);
    }
    private void Start()
    {
        ShowMessage(true);
    }
}

```
</details>


----
</details>

<details><summary>Прервать метод</summary>
	
----
	
Для прерывания метода мы используем ``return`` - это ключевое слово, которое используется для завершения выполнения метода или возврата значения из этого метода.

<details><summary>Пример</summary>

```
public class ClassName : MonoBehaviour
{
	public int playerMoney = 50; // Количество денег
	public int itemCost = 30;  // Стоимость предмета

	// Метод для проверки, может ли игрок купить предмет
	public bool CanPurchaseItem()
    	{
	        // Если у игрока достаточно денег, возвращаем true
	        if (playerMoney >= itemCost)
	        {
	            return true; // Выход из метода с значением true
	        }
	        else
	        {
	            return false; // Выход из метода с значением false
	        }
    	}

    private void Start()
    {
        // Проверяем, может ли игрок купить предмет
        if (CanPurchaseItem()) // Для понимания это то же самое что и CanPurchaseItem()==true
        {
            Debug.Log("Вы можете купить предмет!");
        }
        else
        {
            Debug.Log("У вас недостаточно денег для покупки предмета.");
        }
    }

}
```

</details>

----
</details>

<details><summary>Дополнительно</summary>
	
----
	
<details><summary>Перегрузка метода</summary>

----

Это возможность создавать несколько методов с одним и тем же именем, но с различными аргументами. Это позволяет использовать одно и то же имя метода для выполнения схожих, но немного различных задач. 

Перегрузка методов помогает сделать код более читаемым и удобным.
```
public class ClassName : MonoBehaviour
{
	public int FunctionName(int a, int b)
	{
	        return a + b;
	}

	public float FunctionName(float a, float b)
	{
	        return a + b;
	}
	
	public int FunctionName(int a, int b, int c)
	{
	        return a + b + c;
	}
	public string FunctionName(string a, string b)
	{
		string с = " - это дополнительный текст"
	        return a + b + c;
	}
	private void Start()
	{
		int sumInt = FunctionName(5,6);
		float sumFloat = FunctionName(2.5f, 3.5f);
		int sumThreeInts = FunctionName(1, 2, 3);
		string stringText = FunctionName("Привет ", "мир");
		Debug.Log("Сумма двух целых чисел: " + sumInt);
	        Debug.Log("Сумма двух чисел с плавающей запятой: " + sumFloat);
	        Debug.Log("Сумма трех целых чисел: " + sumThreeInts);
		Debug.Log(stringText);
	}
}

```

----
</details>

----

</details>

## Условия

```
if (условие1)
{
	// Код, выполняемый, если условие1 истина
}
else if (условие2) 
{
	// Код, выполняемый, если условие1 = ложь, но условие2 = истина
}
else if (условие3) 
{
	// Код, выполняемый, если условие2 = ложь, но условие3 = истина
}
else 
{
	// Код, выполняемый, если все условия ложные
}
```
