# Памятка по Unity C#
***
## Переменные
Для объявления переменных используется следующий синтаксис:

**[Атрибут] МодификаторДоступа Тип Название**

<details><summary>Атрибут</summary>

----
Является не обязательным для указания, а нужен чтобы добавить переменной  какие-то свойства

Указывается внутри [ ]

Например атрибут позволяющий  сделать переменную видимой в ``инспекторе``
```
[SerializeField]
```

----
</details>

<details><summary>Модификаторы доступа</summary>
	
----
Используется для обозначения доступности переменной из других классов (скриптов)

На данный момент используем два основных модификатора доступа

Модификатор указывающий на то, что к нашей переменной могут обращаться извне, а также позволяющий видеть нашу переменную в окне инспектора
```
public
```

Модификатор скрывающий переменную от остальных классов
```
private
```
Модификатор доступа не является обязательным атрибутом, если его не указать то будет использован модификатор ``private``

----
</details>

<details><summary>Тип</summary>

----
Указывает на тип переменной, это может быть любой доступный тип

Например типы из C#:

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

Целочисленная переменная с именем `count` доступная другим классам и отображаемая в инспекторе
```
public int count;
```
Переменная с числом с плавающей точкой именем `speed` доступная другим классам и отображаемая в инспекторе
```
public float speed;
```

Переменная ссылающаяся на объект сцены `GameObject`, не доступная другим классам, но отображаемая в инспекторе
```
[SerializeField] private GameObject target;
```

Логическая переменная не доступная другим классам и не отображаемая в инспекторе
```
private bool isCheck;
```

## Методы
Для объявления метода используется следующий синтаксис:

**МодификаторДоступа ВозвращаемыйТип Название**

`void` — это специальный тип методов, который говорит, что метод ничего не возвращает 
```
public void FunctionName() 
{
	// Код выполняемый функцией
}
```

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
