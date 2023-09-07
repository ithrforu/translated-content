---
title: isNaN
slug: Web/JavaScript/Reference/Global_Objects/isNaN
---

{{jsSidebar("Objects")}}

## Аннотация

Функция **`isNaN()`** определяет является ли литерал или переменная нечисловым значением ({{jsxref("Global_Objects/NaN", "NaN")}}) или нет. При работе с функцией необходимо проявлять осторожность так как она [имеет свои особенности](#Description). В качестве альтернативы можно использовать метод {{jsxref("Number.isNaN()")}} из ECMAScript 6, или дополнительно проверять литерал или переменную на нечисловое значение при помощи [`typeof`](/ru/docs/Web/JavaScript/Reference/Operators/typeof).

## Синтаксис

```
isNaN(значение)
```

### Параметры

- `Значение`
  - : Литерал или переменная которые будут проверяться на нечисловое значение.

## Описание

### Для чего нужна функция `isNaN`?

В отличие от других возможных значениях в JavaScript, при работе с значением данного типа невозможно полагаться на == и === для определения, является ли переменная или литерал нечисловым значением ({{jsxref("Global_Objects/NaN", "NaN")}}) или нет, так как проверки `NaN == NaN` и `NaN === NaN` _в качестве значения вернут_ `false`. Следовательно, для проверки нужна функция `isNaN`.

#### Примечание

Для альтернативной проверки переменной на NaN без использования функции isNaN() можно воспользоваться конструкцией x !== x

```
var x = NaN

x != x // true
x !== x // true
```

### Генерация значения `NaN`

Значение `NaN` генерируются арифметическими операциями, результатом которых является _undefined_ или _unrepresentable_. Такие условия не обязательно обозначают переполнение стека. `NaN` также может являться результатом попытки преобразования числа в строку, или значения, не имеющего эквивалента в простых числовых примитивах.

Например, деление нуля на нуль возвращает `NaN` — _но деление других чисел на 0 не возвращает NaN_.

```
var x = NaN

x != x // true
x !== x // true
```

### _Особенности поведения_

С самых ранних версий функции `isNaN` её поведение для не числовых переменных или литералов было довольно-таки запутанным. Когда аргументом функции `isNaN` является переменная, тип которой не [Number](http://es5.github.com/#x8.5), она преобразуется к типу `Number`. Полученное значение затем проверяется, является ли оно {{jsxref("Global_Objects/NaN", "NaN")}}. Таким образом для не числовых значений, которые можно преобразовать в числовой тип без не-NaN значения (в частности, пустая строка или логические примитивы, которые преобразуются в 0 или 1), возвращаемое значение "false" может быть полной неожиданностью; пустая строка преобразуется в "not a number." Путаница связана с тем, что "not a number" имеет определённое значение, описанное в стандарте IEEE-794 чисел с плавающей точкой. Функцию стоит воспринимать в качестве ответа на вопрос, "Является ли это значение корректным числом по стандарту IEEE-794?"

В следующей версии ECMAScript (ES6) функция {{jsxref("Number.isNaN()")}} также присутствует. `Number.isNaN(x)` будет надёжным методом для проверки, содержит ли `x` значение `NaN` или нет. Даже с `Number.isNaN`, однако, результатом `NaN` остаётся точное числовое значение, а не просто "not a number".

## Пример

```js
isNaN(NaN); // true
isNaN(undefined); // true
isNaN({}); // true

isNaN(true); // false
isNaN(null); // false
isNaN(37); // false

// strings
isNaN("37"); // false: "37" преобразуется в число 37 которое не NaN
isNaN("37.37"); // false: "37.37" преобразуется в число 37.37 которое не NaN
isNaN(""); // false: пустая строка преобразуется в 0 которое не NaN
isNaN(" "); // false: строка с пробелом преобразуется в 0 которое не NaN
isNaN("37,5"); // true

// Даты
isNaN(new Date()); // false
isNaN(new Date().toString()); // true

// Пример почему использование isNaN не всегда уместно
isNaN("blabla"); // true: "blabla" преобразовано в число.
// При парсинге преобразуется в число при неудаче возвращает NaN
```

## Спецификация

{{Specifications}}

## Поддержка браузерами

{{Compat}}

## Смотрите также

- {{jsxref("Global_Objects/NaN", "NaN")}}
- {{jsxref("Number.isNaN()")}}