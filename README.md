# Памятка по Unity C#
***
## Содержание
- [Переменные](#переменные)
- [Методы](#методы)
- [Условия](#условия)
- [Циклы](#циклы)
- [Массивы и списки](#массивы-и-списки)

----

## Переменные
Для объявления переменных используется следующий синтаксис:

**[Атрибут] МодификаторДоступа Тип Название**

<details>
<summary>Атрибут</summary>

----
Является не обязательным для указания, а нужен, чтобы добавить переменной какие-то свойства

Указывается внутри [ ]

Например атрибут позволяющий  сделать переменную видимой в ``инспекторе``:
```csharp
[SerializeField]
```

----
</details>

<details><summary>Модификаторы доступа</summary>
	
----
Используется для обозначения доступности переменной из других классов (скриптов)

На данный момент используем два основных модификатора доступа

Модификатор, указывающий на то, что к нашей переменной могут обращаться извне, а также позволяющий видеть нашу переменную в окне инспектора:
```csharp
public
```

Модификатор, скрывающий переменную от остальных классов:
```csharp
private
```
Модификатор доступа не является обязательным атрибутом, если его не указать то будет использован модификатор ``private``

----
</details>

<details markdown='1'>
<summary>Тип</summary>

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
```csharp
public int count;
```
Переменная с числом с плавающей точкой с именем `speed`, доступная другим классам и отображаемая в инспекторе:
```csharp
public float speed;
```

Переменная, ссылающаяся на объект сцены `GameObject`, не доступная другим классам, но отображаемая в инспекторе:
```csharp
[SerializeField] private GameObject target;
```

Логическая переменная, не доступная другим классам и не отображаемая в инспекторе:
```csharp
private bool isCheck;
```

## Методы
Синтаксис написания метода: **МодификаторДоступа ВозвращаемыйТип Название (Аргумент)**

`void` — это специальный тип методов, который говорит, что метод ничего не возвращает 
```csharp
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

```csharp
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
```csharp
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
```csharp
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
```csharp
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
	
```csharp
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

```csharp
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

```csharp
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

```csharp
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

```csharp
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

```csharp
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


<details><summary>Возвращаемый тип</summary>

----
Возвращаемым типом может быть любой имеющийся тип, например:

* `bool` — это тип метода, который возвращает только true (Правда) или false (Ложь)

* `int` — это тип метода, который возвращает целое число (Пример: 2)

* `float` — это тип метода, который возвращает число с плавающей запятой (137.5f == 137,52323)
  
* `string` — это тип метода, который  просто возвращает текст
  
<details><summary>Примеры</summary> 
	
```csharp
public class ClassName : MonoBehaviour
{

	public bool FunctionName()
	{
		return  false;
	}

	private void Start()
	{

		Debug.Log("Мы получили " + FunctionName());
		
	}

}
```

```csharp
public class ClassName : MonoBehaviour
{
	public int money = 15;
	public int FunctionName()
	{
		return  10; 
	}

	private void Start()
	{
		Debug.Log("Сумма " + FunctionName() + " и у вас " + money + " денег.");
	}
}
```

```csharp
public class ClassName : MonoBehaviour
{
	public float FunctionName()
	{
	        return 127.5f;
	}
	private void Start()
	{

	Debug.Log("Всё работает на " + FunctionName()+ " %");
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
```csharp
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

В `C#` есть несколько проверок условий:

* `if` - проверяет первое условие
* `else if` -  Не обязателен, проверяет следующие условия, если предыдущее условие ложно
* `else` - Не обязателен, выполняет блок кода, если все предыдущие условия ложны

Эти конструкции используются для того, чтобы выбрать, какой из путей кода следует выполнять на основе логического выражения.

<details><summary>Конструкция условий</summary>

----

После написания `if` обязательно ставим `(условие)`, так как в скобках пишется условие. Также, если вы написали `else if`, то также обязательно ставим `(условие)`.

Если используется `else if`, то он обязательно дожен быть после `if`, но  до `else`!

Количество условий с `else if` может быть любым.

Если после этого можно вызвать `else`, делаем без условий.

----
</details>

```csharp
if (условие1)
{
	// Код, выполняемый, если условие1 = истина
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

<details><summary>Логические операции</summary>

----

Для проверки нескольких условий существует символы: 
* `&&` - оператор И
* `||` - оператор ИЛИ
* `!` - оператор НЕ


**Пример 1**

В представленном примере мы храним результат логической операции в булевой переменной.

Если хотя бы одно из условий выполнено, то булевая переменная примет значение  `true` (истина). Если же ни одно из условий не будет выполнено, то переменная получит значение `false` (ложь).

```csharp
	public int a = 6;
    	public int w = 2;
    	void Start()
    	{
        	bool demo1 = a > 5 || w < 9;
        	Debug.Log("Результат qweqw0: " + demo1);

        	bool demo2 = a > 5 && w == 9;
        	Debug.Log("Результат demo1: " + demo2);

        	bool demo3 = a > 5 && w != 9;
        	Debug.Log("Результат qweqw2: " + demo3);

    	}
```

**Пример 2**

В данном примере мы используем условные операторы `if` для проверки различных условий.

```csharp

    	public int a = 4; // Объявляем переменную a и присваиваем ей значение 4
    	public int w = 10; // Объявляем переменную w и присваиваем ей значение 10
	void Start()
    	{
		// Проверяем, выполняется ли хотя бы одно из условий: a больше 5 или w меньше 9
        	if (a > 5 || w < 9)
        	{
			 // Если одно из условий истинно, выводим сообщение
            		Debug.Log("Результат истина");
        	}	

        	else 
        	{
			// Если оба условия ложны, выводим другое сообщение
            		Debug.Log("Результат ложь");
        	}

		// Создаем булевую переменную demo1, которая будет истинна только если a меньше 5 и w не равно 9
        	bool demo1 = a < 5 && w != 9;
        	if(demo1)
        	{
			// Если demo1 истинно, выводим сообщение
            		Debug.Log("Результат истина");
        	}
        	else
        	{
			// Если demo1 ложно, выводим другое сообщение
            		Debug.Log("Результат ложь");
        	}       

    	}

```

----

</details>


<details><summary>Использование условий на практике</summary>

**Пример 1**
 
Проверка на количества здоровья у персонажа.

```csharp

public int health = 100;

void Update()
{
	if (health > 75)
        {
            Debug.Log("Здоровье в порядке!");
        }
        else if (health > 50)
        {
            Debug.Log("Здоровье на среднем уровне.");
        }
        else if (health > 25)
        {
            Debug.Log("Здоровье низкое!");
        }
        else
        {
            Debug.Log("Персонаж на грани смерти!");
        }
}

```

**Пример 2**

Проверка на включенный буст для добавления скорости. 

```csharp

public int baseSpeed = 5;
public bool speedBoostActive = false;
public float speedBoostMultiplier = 2.0f;

void Update()
{
	float currentSpeed = baseSpeed;

        if (speedBoostActive)
        {
            currentSpeed *= speedBoostMultiplier;
            Debug.Log("Буст скорости активен! Текущая скорость: " + currentSpeed);
        }
        else
        {
            Debug.Log("Текущая скорость: " + currentSpeed);
        }

        // Для тестирования
        if (Input.GetKeyDown(KeyCode.B))
        {
            speedBoostActive = !speedBoostActive;
        }
}

```

**Пример 3**

Проверка количества денег и времени 

```csharp

public float time = 20;

public float money = 100;


void Start()
{
        
	bool CancelTime = time >= 100 || time < money;
        if(CancelTime)
        {
            if (money >= 100 && time==0) 
            {
                Debug.Log("Деньги есть, времени нет");
            }
            else if (money >= 100 && time>=0)
            {
                Debug.Log("Деньги есть, времени много");
            }
            else 
            {
                Debug.Log("Чего то не хватает");
            }
        }
        else
        {
            Debug.Log("Много чего не хватает");
        }   
}

```
</details>


## Циклы

Циклы позволяют многократно выполнять один и тот же код.

Пример цикла, который повторится 10 раз:
```csharp
for (int i = 0; i < 10; i++)
{
	// Код выполняемый в цикле
	Debug.Log("Hello");
}

```
Пояснениие: 
* `int i = 0` - Начни с числа 0
* `i < 10` - Работай пока `i` будет меньше 10
* `i++` - После каждой итерации добавляй 1 к числу `i`
В результате работы код выведет 10 раз строку "Hello" в консоль

**Как это работает?**

При объявлении цикла `for` в скобках обычно указывается:
* Перменная цикла `int i = 0`. Название, тип и стартовое значение может быть любым.
* Условие цикла `i < 10`. Условие так же может быть чем угодно у чего результать будет булевый (`bool`) тип (`true` или `false`).
* Действие выполняемое после завершения итерации цикла `i++`. Может быть любая математическая операция или вызов метода.
* То что находится внутри `{}` идущих после объявления `for` будет выполняться столько раз, сколько выполнится цикл

## Массивы и списки

### Массивы

Массив — это набор данных одного типа, который имеет фиксированный размер. Массив создаётся с заранее заданным количеством элементов, и его размер нельзя изменить после создания.

**Синтаксис:**

```csharp
Тип[] Название = new Тип[Размер];
```

**Обращение к элементам:**

- Элементы массива доступны по индексу, начиная с 0.
- Используй `Название[индекс]` для чтения или записи значения.

**Пример:**

```csharp
int[] numbers = new int[3]; // Массив из 3 целых чисел
numbers[0] = 10; // Установить первый элемент
numbers[1] = 20; // Установить второй элемент
numbers[2] = 30; // Установить третий элемент
Debug.Log(numbers[1]); // Вывод: 20
```

**Особенности:**

- Индекс начинается с 0 (первый элемент — `[0]`).
- Размер массива фиксирован, его нельзя увеличить или уменьшить.
- Подходит, когда точно знаешь количество элементов.

**Особенности:**

- Доступ к элементам по индексу (начинается с 0).
- Размер массива фиксирован, его нельзя увеличить или уменьшить.
- Подходит, когда точно знаешь количество элементов.

### Списки

Список — это динамический набор данных одного типа. В отличие от массива, список может увеличиваться или уменьшаться в размере.

**Синтаксис:**

```csharp
List<Тип> Название = new List<Тип>();
```
**Обращение к элементам:**

- Как и в массивах, используй `Название[индекс]` для доступа к элементам.
- Можно добавлять элементы с помощью `Add` или удалять с помощью `Remove`.

**Пример:**

```csharp
List<string> names = new List<string>(); // Пустой список строк
names.Add("Арсений"); // Добавить элемент
names.Add("Данил"); // Добавить ещё один
names.Remove("Арсений"); // Удалить элемент
Debug.Log(names[0]); // Вывод: Данил
```

<details><summary>Полезные методы</summary>

**Основные методы списков:**

- `Add(элемент)` — добавляет элемент в конец списка.
- `Remove(элемент)` — удаляет первое вхождение указанного элемента.
- `RemoveAt(индекс)` — удаляет элемент по указанному индексу.
- `Clear()` — удаляет все элементы из списка.
- `Count` — возвращает количество элементов в списке (не метод, а свойство).

**Пример использования методов:**

```csharp
List<int> scores = new List<int>();
scores.Add(100); // Добавить 100
scores.Add(200); // Добавить 200
scores.Remove(100); // Удалить 100
scores.RemoveAt(0); // Удалить элемент по индексу 0
Debug.Log(scores.Count); // Вывод: 0
scores.Clear(); // Очистить список
```

</details>

**Особенности:**

- Доступ к элементам по индексу, как в массиве.
- Можно добавлять (`Add`) и удалять (`Remove`) элементы.
- Подходит, когда количество элементов может меняться.

### Разница между массивами и списками

| **Массив** | **Список** |
| --- | --- |
| Фиксированный размер | Динамический размер |
| Нельзя изменить после создания | Можно добавлять/удалять элементы |
| `int[] numbers = new int[3];` | `List<int> numbers = new List<int>();` |
| Быстрее для фиксированных данных | Удобнее для изменяемых данных |

**Когда использовать:**

- Используй **массив**, если количество элементов известно и не изменится (например, 4 колеса машины).
- Используй **список**, если количество элементов может меняться (например, список врагов в игре).

**Пример в Unity:**

```csharp
public class Inventory : MonoBehaviour
{
    public string[] inventorySlots = new string[3]; // Массив для 3 слотов инвентаря
    public List<string> collectedItems = new List<string>(); // Список собранных предметов

    void Start()
    {
        // Заполняем массив слотов инвентаря
        inventorySlots[0] = "Меч";
        inventorySlots[1] = "Щит";
        inventorySlots[2] = "Зелье";
        Debug.Log("Первый слот: " + inventorySlots[0]); // Вывод: Меч

        // Добавляем предметы в список
        collectedItems.Add("Кольцо");
        collectedItems.Add("Амулет");
        Debug.Log("Собранный предмет: " + collectedItems[0]); // Вывод: Кольцо
    }
}
```
