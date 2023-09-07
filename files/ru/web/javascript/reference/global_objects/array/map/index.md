---
title: Array.prototype.map()
slug: Web/JavaScript/Reference/Global_Objects/Array/map
---

{{JSRef("Global_Objects", "Array")}}

## Сводка

Метод **`map()`** создаёт новый массив с результатом вызова указанной функции для каждого элемента массива.

## Синтаксис

```
const new_array = arr.map(function callback( currentValue[, index[, array]]) {
    // Возвращает элемент для new_array
}[, thisArg])
```

### Параметры

- `callback`

  - : Функция, вызываемая для каждого элемента массива `arr`. Каждый раз, когда `callback` выполняется, возвращаемое значение добавляется в `new_array`.

    Функция `callback`, создающая элемент в новом массиве, принимает три аргумента:

    - `currentValue`
      - : Текущий обрабатываемый элемент массива.
    - `index`{{optional_inline}}
      - : Индекс текущего обрабатываемого элемента в массиве.
    - `array`{{optional_inline}}
      - : Массив, по которому осуществляется проход.

- `thisArg`{{optional_inline}}
  - : Необязательный параметр. Значение, используемое в качестве `this` при вызове функции `callback`

### Возвращаемое значение

Новый массив, где каждый элемент является результатом `callback` функции.

## Описание

Метод `map` вызывает переданную функцию `callback` один раз для каждого элемента, в порядке их появления и конструирует новый массив из результатов её вызова. Функция `callback` вызывается только для индексов массива, имеющих присвоенные значения, включая {{jsxref("Global_Objects/undefined", "undefined")}}. Она не вызывается для пропущенных элементов массива (то есть для индексов, которые никогда не были заданы, которые были удалены или которым никогда не было присвоено значение.

Функция `callback` вызывается с тремя аргументами: значением элемента, индексом элемента и массивом, по которому осуществляется проход.

Если в метод `map` был передан параметр `thisArg`, при вызове `callback` он будет использоваться в качестве значения `this`. В противном случае в качестве значения `this` будет использоваться значение {{jsxref("Global_Objects/undefined", "undefined")}}. В конечном итоге, значение `this`, наблюдаемое из функции `callback`, определяется согласно [обычным правилам определения `this`, видимого из функции](/ru/docs/Web/JavaScript/Reference/Operators/this).

Метод `map` не изменяет массив, для которого он был вызван (хотя функция `callback` может это делать).

Диапазон элементов, обрабатываемых методом `map`, устанавливается до первого вызова функции `callback`. Элементы, добавленные в массив после начала выполнения метода `map`, не будут посещены функцией `callback`. Если существующие элементы массива изменяются функцией `callback`, их значения, переданные в функцию, будут значениями на тот момент времени, когда метод `map` посетит их; удалённые элементы посещены не будут.

## Примеры

### Пример: отображение массива чисел на массив квадратных корней

Следующий код берёт массив чисел и создаёт новый массив, содержащий квадратные корни чисел из первого массива.

```js
const numbers = [1, 4, 9];
const roots = numbers.map(Math.sqrt);
// теперь roots равен [1, 2, 3], а numbers всё ещё равен [1, 4, 9]
```

### Пример: отображение массива чисел с использованием функции, содержащей аргумент

Следующий код показывает, как работает отображение, когда функция требует один аргумент. Аргумент будет автоматически присваиваться каждому элементу массива, когда `map` проходит по оригинальному массиву.

```js
const numbers = [1, 4, 9];
const doubles = numbers.map((num) => num * 2);
// теперь doubles равен [2, 8, 18], а numbers всё ещё равен [1, 4, 9]
```

### Пример: обобщённое использование `map`

Этот пример показывает, как использовать `map` на объекте строки {{jsxref("Global_Objects/String", "String")}} для получения массива байт в кодировке ASCII, представляющего значения символов:

```js
const map = Array.prototype.map;
const charCodes = map.call("Hello World", (x) => x.charCodeAt(0));
// теперь charCodes равен [72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100]
```

### Пример: обобщённое использование `map` вместе с `querySelectorAll`

Этот пример показывает, как пройтись по коллекции объектов, собранных с помощью `querySelectorAll`. В данном случае мы получаем все выбранные опции на экране и печатаем их в консоль:

```js
const elems = document.querySelectorAll("select option:checked");
const values = Array.prototype.map.call(elems, ({ value }) => value);
```

Более простым способом будет использование метода {{jsxref("Array.from()")}}.

### Пример: использование `map` для переворачивания строки

```js
const string = "12345";
const reversed = Array.prototype.map
  .call(string, (x) => x)
  .reverse()
  .join("");
// reversed равен '54321'
// Бонус: используйте '===' для проверки того, является ли строка палиндромом
```

Более простым способом будет использование метода {{jsxref("String.split()")}} (см. пример [обращение строки при помощи метода split()](/ru/docs/Web/JavaScript/Reference/Global_Objects/String/split#Example:_Reversing_a_String_using_split)).

### Пример: хитрый вариант использования

[(навеяно этой записью в блоге)](http://www.wirfs-brock.com/allen/posts/166)

Распространённой практикой является использование колбэк-функции с одним аргументом (элемент, над которым производится операция). Некоторые функции также широко используется с одним аргументом, хотя они принимают дополнительные необязательные аргументы. Эти привычки могут привести к неожиданному поведению программы.

```js
// Рассмотрим пример:
["1", "2", "3"].map(parseInt);
// Хотя ожидаемый результат вызова равен [1, 2, 3],
// в действительности получаем [1, NaN, NaN]

// Функция parseInt часто используется с одним аргументом, но она принимает два.
// Первый аргумент является выражением, а второй - основанием системы счисления.
// В функцию callback Array.prototype.map передаёт 3 аргумента:
// элемент, его индекс и сам массив.
// Третий аргумент игнорируется parseInt, но не второй, следовательно,
// возможна путаница. Смотрите запись в блоге для дополнительной информации.

const returnInt = (element) => parseInt(element, 10);

["1", "2", "3"].map(returnInt);
// Результатом является массив чисел (как и ожидалось)

// Простейший способ добиться вышеозначенного поведения и избежать чувства "чё за!?":
["1", "2", "3"].map(Number); // [1, 2, 3]
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- [Polyfill of Array.prototype.map in core-js](https://github.com/zloirock/core-js#ecmascript-array)
- {{jsxref("Array.prototype.forEach()")}}
- объект {{jsxref("Map")}}
- {{jsxref("Array.from()")}}