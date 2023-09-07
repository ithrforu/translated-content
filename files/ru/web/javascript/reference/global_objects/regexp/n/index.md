---
title: RegExp.$1-$9
slug: Web/JavaScript/Reference/Global_Objects/RegExp/n
---

{{JSRef}} {{non-standard_header}}

Нестандартные свойства **$1, $2, $3, $4, $5, $6, $7, $8, $9** являются статическими и доступными только для чтения свойствами регулярных выражений, которые содержат найденные подстроки, обёрнутые в скобки.

## Синтаксис

```
RegExp.$1
RegExp.$2
RegExp.$3
RegExp.$4
RegExp.$5
RegExp.$6
RegExp.$7
RegExp.$8
RegExp.$9
```

## Описание

Свойства $1, ..., $9 являются статичными, они не являются свойствами конкретного объекта регулярного выражения, поэтому вы всегда можете использовать их как `RegExp.$1`, ..., `RegExp.$9`.

Значения этих свойств не доступны для изменения, они модифицируются всякий раз при успешном совпадении регулярного выражения.

Количество возможных подстрок в круглых скобках неограничено, но объект `RegExp` может содержать в себе только последние 9. Вы можете получить доступ ко всем подстрокам, совпавшим с выражениями внутри круглых скобок, с помощью индексов возвращённого массива.

Эти свойства могу использоваться при замене текста в методе {{jsxref("String.replace")}}. Когда используете его, не добавляйте их в `RegExp`. Пример ниже демонстрирует правильное применение. Когда круглые скобки не включены в регулярное выражение, код интерпретирует такие значения, как `$n` буквально, как литерал (n - положительное число).

## Примеры

### Использование `$n` со `String.replace`

Следующий код использует метод {{jsxref("String.prototype.replace()", "replace()")}} строки {{jsxref("String")}}, чтобы преобразовать строку в формате _Имя Фамилия_ в формат _Фамилия, Имя_. В коде замены текста используются `$1` и `$2` чтобы указать порядок вывода результата совпадений полученных при сравнивании с шаблоном регулярного выражения, имеющего круглые скобки.

```js
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
str.replace(re, "$2, $1"); // "Smith, John"
RegExp.$1; // "John"
RegExp.$2; // "Smith"
```

## Спецификация

Не стандартизированной. Не является частью какой-либо спецификации

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- {{non-standard_inline}} {{jsxref("RegExp.input", "RegExp.input ($_)")}}
- {{non-standard_inline}} {{jsxref("RegExp.lastMatch", "RegExp.lastMatch ($&amp;)")}}
- {{non-standard_inline}} {{jsxref("RegExp.lastParen", "RegExp.lastParen ($+)")}}
- {{non-standard_inline}} {{jsxref("RegExp.leftContext", "RegExp.leftContext ($`)")}}
- {{non-standard_inline}} {{jsxref("RegExp.rightContext", "RegExp.rightContext ($')")}}