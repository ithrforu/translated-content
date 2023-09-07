---
title: RegExp
slug: Web/JavaScript/Reference/Global_Objects/RegExp
---

{{JSRef("Global_Objects", "RegExp")}}

## Сводка

Конструктор **`RegExp`** создаёт объект регулярного выражения для сопоставления текста с шаблоном.

Введение в то, что представляют собой регулярные выражения, читайте в [главе «Регулярные выражения» в руководстве по JavaScript](/ru/docs/Web/JavaScript/Guide/Regular_Expressions).

{{EmbedInteractiveExample("pages/js/regexp-constructor.html")}}

## Синтаксис

Возможны как литеральная запись, так и запись через конструктор:

```
/pattern/flags
new RegExp(pattern, flags)
```

### Параметры

- `pattern`
  - : Текст регулярного выражения.
- `flags`

  - : Если определён, может принимать любую комбинацию нижеследующих значений:

    - `g`
      - : глобальное сопоставление
    - `i`
      - : игнорирование регистра при сопоставлении
    - `m`
      - : сопоставление по нескольким строкам; символы начала и конца (^ и $) начинают работать по нескольким строкам (то есть, происходит сопоставление с началом или концом _каждой_ строки (строки разделяются символами \n или \r), а не только с началом или концом всей вводимой строки)
    - `y` {{experimental_inline}}
      - : «липкий» поиск; сопоставление в целевой строке начинается с индекса, на который указывает свойство `lastIndex` этого регулярного выражения (и не пытается сопоставиться с любого более позднего индекса).

## Описание

Существует два способа создания объекта `RegExp`: литеральная запись и использование конструктора. При записи строк параметры в литеральной записи не используют символы кавычек, в то время как параметры функции-конструктора используют кавычки. Так что следующие выражения создают одинаковые регулярные выражения:

```js
/ab+c/i;
new RegExp("ab+c", "i");
```

Литеральная запись обеспечивает компиляцию регулярного выражения при вычислении выражения. Используйте литеральную запись если регулярное выражение будет неизменным. Например, если вы используете литеральную запись для конструирования регулярного выражения, используемого в цикле, регулярное выражение не будет перекомпилироваться на каждой итерации.

Конструктор объекта регулярного выражения, например, `new RegExp('ab+c')`, обеспечивает компиляцию регулярного выражения во время выполнения. Используйте функцию-конструктор, если вы знаете, что шаблон регулярного выражения будет меняться или если вы не знаете шаблон и получаете его из внешних источников, например, из пользовательского ввода.

При использовании функции-конструктора необходимо использовать обычные правила экранирования в строках (предварять специальные символы символом обратного слеша «\»). Например, следующие выражения эквивалентны:

```js
var re = /\w+/;
var re = new RegExp("\\w+");
```

## Значение специальных символов в регулярных выражениях

- [Символьные классы](#character-classes)
- [Наборы символов](#character-sets)
- [Границы](#boundaries)
- [Группировка и обратные ссылки](#grouping-back-references)
- [Квантификаторы](#quantifiers)

<table class="fullwidth-table">
  <tbody>
    <tr id="character-classes">
      <th colspan="2">Символьные классы</th>
    </tr>
    <tr>
      <th>Символ</th>
      <th>Значение</th>
    </tr>
    <tr>
      <td><code>.</code></td>
      <td>
        <p>
          (Точка, десятичная запятая) сопоставляется с любым символом
          <em>за исключением</em> символов новой строки: <code>\n</code>,
          <code>\r</code>, <code>\u2028</code> или <code>\u2029</code>.
        </p>
        <p>
          Обратите внимание, что флаг многострочности <code>m</code> не изменяет
          поведение точки. Так что для сопоставления с шаблона с несколькими
          строками используйте набор символов <code>[^]</code> (конечно, если
          только вам не нужно поддерживать старые версии IE), он сопоставляется
          с любым символом, включая символы новой строки.
        </p>
        <p>
          Например, шаблон <code>/.н/</code> сопоставляется с подстрокой «ан»,
          но не подстрокой «ну», во фразе «ну что, потанцуем».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\d</code></td>
      <td>
        <p>
          Сопоставляется с символом цифры в базовом латинском алфавите.
          Эквивалентен набору символов <code>[0-9]</code>.
        </p>
        <p>
          Например, шаблоны <code>/\d/</code> и
          <code>/[0-9]/</code> сопоставляются с подстрокой «2» в строке «B2 —
          это номер люкс».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\D</code></td>
      <td>
        <p>
          Сопоставляется с любым символом, который не является цифрой в базовом
          латинском алфавите. Эквивалентен набору символов <code>[^0-9]</code>.
        </p>
        <p>
          Например, шаблоны <code>/\D/</code> и
          <code>/[^0-9]/</code> сопоставляются с подстрокой «B» в строке «B2 —
          это номер люкс».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\w</code></td>
      <td>
        <p>
          Сопоставляется с любым алфавитно-цифровым символом из базового
          латинского алфавита, включая символ подчёркивания. Эквивалентен набору
          символов <code>[A-Za-z0-9_]</code>.
        </p>
        <p>
          Например, шаблон <code>/\w/</code> сопоставляется с подстрокой «a» в
          строке «apple», с подстрокой «5» в строке «$5.28» и с подстрокой «3» в
          строке «3D».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\W</code></td>
      <td>
        <p>
          Сопоставляется с любым символом из базового латинского алфавита, не
          являющимся символом, из которых состоят слова. Эквивалентен набору
          символов <code>[^A-Za-z0-9_]</code>.
        </p>
        <p>
          Например, шаблоны <code>/\W/</code> и
          <code>/[^A-Za-z0-9_]/</code> сопоставляются с подстрокой «%» в строке
          «50%».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\s</code></td>
      <td>
        <p>
          Сопоставляется с одиночным пробельным символом, который включает в
          себя пробел, табуляцию, подачу страницы, перевод строки и другие
          пробельные символы Юникода. Эквивалентен набору символов
          <code
            >[
            \f\n\r\t\v\u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u2028\u2029\u202f\u205f\u3000]</code
          >.
        </p>
        <p>
          Например, шаблон <code>/\s\w*/</code> сопоставляется с подстрокой «
          bar» в строке «foo bar».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\S</code></td>
      <td>
        <p>
          Сопоставляется с одиночным символом, не являющимся пробельным.
          Эквивалентен набору символов
          <code
            >[^
            \f\n\r\t\v\u00a0\u1680\u180e\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u2028\u2029\u202f\u205f\u3000]</code
          >.
        </p>
        <p>
          Например, шаблон <code>/\S\w*/</code> сопоставляется с подстрокой
          «foo» в строке «foo bar».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\t</code></td>
      <td>Сопоставляется с символом табуляции.</td>
    </tr>
    <tr>
      <td><code>\r</code></td>
      <td>Сопоставляется с символом возврата каретки.</td>
    </tr>
    <tr>
      <td><code>\n</code></td>
      <td>Сопоставляется с символом перевода строки.</td>
    </tr>
    <tr>
      <td><code>\v</code></td>
      <td>Сопоставляется с символом вертикальной табуляции.</td>
    </tr>
    <tr>
      <td><code>\f</code></td>
      <td>Сопоставляется с символом подачи страницы.</td>
    </tr>
    <tr>
      <td><code>[\b]</code></td>
      <td>
        Сопоставляется с символом забоя (не перепутайте его с символьным классом
        <code>\b</code>).
      </td>
    </tr>
    <tr>
      <td><code>\0</code></td>
      <td>
        Сопоставляется с нулевым символом. Не ставьте за ним другую цифру.
      </td>
    </tr>
    <tr>
      <td>
        <code>\c<em>X</em></code>
      </td>
      <td>
        <p>
          Где <code><em>X</em></code> является буквой от «A» до «Z».
          Сопоставляется с управляющим символом в строке.
        </p>
        <p>
          Например, шаблон <code>/\cM/</code> сопоставляется с символом
          control-M в строке.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code>\x<em>hh</em></code>
      </td>
      <td>
        Сопоставляется с символом с кодом <code><em>hh</em></code> (две
        шестнадцатеричные цифры).
      </td>
    </tr>
    <tr>
      <td>
        <code>\u<em>hhhh</em></code>
      </td>
      <td>
        Сопоставляется с символом со значением Юникода
        <code><em>hhhh</em></code> (четыре шестнадцатеричные цифры).
      </td>
    </tr>
    <tr>
      <td><code>\</code></td>
      <td>
        <p>
          Для символов, которые обычно трактуются буквально, указывает, что
          следующий символ является специальным и не должен интерпретироваться
          буквально.
        </p>
        <p>
          Например, шаблон <code>/b/</code> сопоставляется с символом «b».
          Поместив перед ним символ обратного слеша, то есть превратив шаблон в
          <code>/\b/</code>, символ приобретёт специальное значение,
          обозначающее сопоставление с границей слова.
        </p>
        <p><em>или</em></p>
        <p>
          Для символов, которые обычно трактуются специальным образом,
          указывает, что следующий символ не является специальным и должен
          интерпретироваться буквально.
        </p>
        <p>
          Например, звёздочка «*» является специальным символом, обозначающим
          ноль или более вхождений предшествующего символа при сопоставлении;
          поэтому шаблон <code>/a*/</code> означает сопоставление с нулём или
          более символов «a». Для буквального сопоставления со звёздочкой
          <code>*</code> предварите её символом обратного слеша; например,
          шаблон <code>/a\*/</code> сопоставляется со строкой «a*».
        </p>
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr id="character-sets">
      <th colspan="2">Наборы символов</th>
    </tr>
    <tr>
      <th>Символ</th>
      <th>Значение</th>
    </tr>
    <tr>
      <td><code>[xyz]</code></td>
      <td>
        <p>
          Набор символов. Сопоставляется с любым из заключённых в квадратные
          скобки символов. С помощью дефиса вы можете определить диапазон
          символов.
        </p>
        <p>
          Например, шаблон <code>[абвгд]</code> означает тоже самое, что и
          шаблон <code>[а-д]</code>. Они сопоставляются с символом «г» в слове
          «грудинка» и символом «б» в слове «отбивная».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>[^xyz]</code></td>
      <td>
        <p>
          Отрицательный или дополнительный набор символов. То есть он
          сопоставляется со всеми символами, что не заключены в квадратные
          скобки. С помощью дефиса вы можете определить диапазон символов.
        </p>
        <p>
          Например, шаблон <code>[^абвгд]</code> означает тоже самое, что и
          шаблон <code>[^а-д]</code>. Они сопоставляются с символом «е» в слове
          «бекон» и символом «о» в слове «отбивная».
        </p>
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr id="boundaries">
      <th colspan="2">Границы</th>
    </tr>
    <tr>
      <th>Символ</th>
      <th>Значение</th>
    </tr>
    <tr>
      <td><code>^</code></td>
      <td>
        <p>
          Сопоставляется c началом ввода. Если установлен флаг многострочности,
          также сопоставляется с позицией сразу за символом переноса строки.
        </p>
        <p>
          Например, шаблон <code>/^Б/</code> не сопоставляется с буквой «Б» в
          строке «буква Б», но сопоставляется с первой буквой «Б» в строке
          «Буква Б».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>$</code></td>
      <td>
        <p>
          Сопоставляется c концом ввода. Если установлен флаг многострочности,
          также сопоставляется с позицией сразу перед символом переноса строки.
        </p>
        <p>
          Например, шаблон <code>/т$/</code> не сопоставляется с буквой «т» в
          слове «кормить», но сопоставляется с ней в слове «кормит».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\b</code></td>
      <td>
        <p>
          Сопоставляется с границей слова нулевой ширины, например с позицией
          между буквой и пробелом (не путайте его с набором символов
          <code>[\b]</code>).
        </p>
        <p>
          Например, шаблон <code>/\bпол/</code> сопоставляется с подстрокой
          «пол» в строке «в полдень»; шаблон <code>/но\b/</code> сопоставляется
          с подстрокой «но» в строке «возможно завтра».
        </p>
      </td>
    </tr>
    <tr>
      <td><code>\B</code></td>
      <td>
        <p>
          Сопоставляется с границей не-слов нулевой ширины, например с позицией
          между двумя буквами или двумя пробелами.
        </p>
        <p>
          Например, шаблон <code>/\Bдень/</code> сопоставляется с подстрокой
          «день» в строке «в полдень»; шаблон <code>/за\B/</code> сопоставляется
          с подстрокой «за» в строке «возможно завтра».
        </p>
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr id="grouping-back-references">
      <th colspan="2">Группировка и обратные ссылки</th>
    </tr>
    <tr>
      <th>Символ</th>
      <th>Значение</th>
    </tr>
    <tr>
      <td><code>(<em>x</em>)</code></td>
      <td>
        <p>
          Сопоставляется с <code><em>x</em></code> и запоминает сопоставление.
          Называется «захватывающие скобки».
        </p>
        <p>
          Например, шаблон <code>/(foo)/</code> сопоставляется с подстрокой
          «foo» и запоминает её в строке «foo bar». Сопоставленную подстроку
          можно достать из элементов <code>[1], ..., [n]</code> результирующего
          массива или из предопределённых свойств
          <code>$1, ..., $9</code> объекта <code>RegExp</code>.
        </p>
        <p>
          Захват групп ведёт к проседанию производительности. Если вам не нужно
          повторно ссылаться на захваченную подстроку, лучше использовать скобки
          без захвата (смотрите ниже).
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code>\<em>n</em></code>
      </td>
      <td>
        <p>
          Где <code><em>n</em></code> является целым положительным числом.
          Обратная ссылка на последнюю сопоставившуюся подстроку в
          <em>n</em>-ных по счёту круглых скобках в регулярном выражении
          (нумерация скобок идёт слева направо).
        </p>
        <p>
          Например, шаблон <code>/яблоко(,)\sапельсин\1/</code> сопоставится
          подстроке «яблоко, апельсин,» в строке «яблоко, апельсин, вишня,
          персик». Более подробный пример смотрите после этой таблицы.
        </p>
      </td>
    </tr>
    <tr>
      <td><code>(?:<em>x</em>)</code></td>
      <td>
        Сопоставляется с <code><em>x</em></code
        >, но не запоминает сопоставление. Называется «незахватывающие скобки».
        Сопоставленную подстроку нельзя достать из элементов
        <code>[1], ..., [n]</code> результирующего массива или из
        предопределённых свойств <code>$1, ..., $9</code> объекта
        <code>RegExp</code>.
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr id="quantifiers">
      <th colspan="2">Квантификаторы</th>
    </tr>
    <tr>
      <th>Символ</th>
      <th>Значение</th>
    </tr>
    <tr>
      <td>
        <code><em>x</em>*</code>
      </td>
      <td>
        <p>
          Сопоставляется с предшествующим элементом <em>x</em> ноль или более
          раз.
        </p>
        <p>
          Например, шаблон <code>/ела*/</code> сопоставляется с подстрокой «ел»
          в строке «Призрак просвистел» и подстрокой «ела» в строке «Птица
          пропела», но ни с чем не сопоставится в строке «Козёл хмыкнул».
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>+</code>
      </td>
      <td>
        <p>
          Сопоставляется с предшествующим элементом <em>x</em> один или более
          раз. Эквивалентен квантификатору <code>{1,}</code>.
        </p>
        <p>
          Например, шаблон <code>/о+/</code> сопоставляется с символом «о» в
          строке «конфета» и со всеми символами «о» в строке «коооооонфета».
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>*?</code><br /><code><em>x</em>+?</code>
      </td>
      <td>
        <p>
          Сопоставляется с предшествующим элементом <em>x</em> подобно
          квантификаторам <code>*</code> и <code>+</code>, описанным выше,
          однако ищет минимально возможное сопоставление.
        </p>
        <p>
          Например, шаблон <code>/".*?"/</code> сопоставляется с подстрокой
          «"foo"» в строке «"foo" "bar"» и не сопоставляется со строкой «"foo"
          "bar"», поскольку за звёздочкой <code>*</code> следует символ вопроса
          <code>?</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>?</code>
      </td>
      <td>
        <p>
          Сопоставляется с предшествующим элементом <em>x</em> ноль или один
          раз.
        </p>
        <p>
          Например, шаблон <code>/о?то?/</code> сопоставляется с подстрокой «от»
          в строке «кот» и подстрокой «то» в строке «ток».
        </p>
        <p>
          Если символ используется сразу после какого-то из квантификаторов
          <code>*</code>, <code>+</code>, <code>?</code>, или <code>{}</code>,
          то он делает этот квантификатор «нежадным» (сопоставление происходит
          минимально возможное количество раз), в противоположность «жадному»
          поведению квантификатора по умолчанию (сопоставление происходит
          максимально возможное количество раз).
        </p>
        <p>
          Также символ используется в квантификаторах предпросмотра
          <code>(?=)</code>, <code>(?!)</code> и <code>(?:)</code>, также
          описанных в этой таблице.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>(?=<em>y</em>)</code>
      </td>
      <td>
        Сопоставляется с <code><em>x</em></code
        >, только если за <code><em>x</em></code> следует <code><em>y</em></code
        >. Например, шаблон <code>/Джек(?=Шпрот)/</code> сопоставляется со
        строкой «Джек» только если за ней следует строка «Шпрот». Шаблон
        <code>/Джек(?=Шпрот|Мороз)/</code> сопоставляется со строкой «Джек»
        только если за ней следуют строки «Шпрот» или «Мороз». Однако, ни
        «Шпрот», ни «Мороз» не являются частью результата сопоставления.
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>(?!<em>y</em>)</code>
      </td>
      <td>
        <p>
          Сопоставляется с <code><em>x</em></code
          >, только если за <code><em>x</em></code> не следует
          <code><em>y</em></code
          >. Например, шаблон <code>/\d+(?!\.)/</code> сопоставляется с числом
          только если за ним не следует десятичная запятая.
        </p>
        <p>
          Выражение <code>/\d+(?!\.)/.exec('3.141')</code> сопоставится с «141»
          но не с «3.141».
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code>(?&#x3C;=<em>y</em>)<em>x</em></code>
      </td>
      <td>
        <p>
          <code
            ><font face="Arial, x-locale-body, sans-serif"
              ><span style="background-color: #ffffff"
                >Сопоставляется с
              </span></font
            ><em>x</em></code
          >, только если <code><em>x</em></code> предшествует
          <code><em>y</em></code>
        </p>
        <p>
          Например, /<code>(?&#x3C;=Пётр)Иванов/</code> сопоставится с "Иванов"
          только если ему будет предшествовать "Петр".<br /><code
            >/(?&#x3C;=Пётр|Владислав)Иванов/</code
          >
          сопоставится с "Иванов" только если ему будет предшествовать "Пётр"
          или "Владислав".<br />В любом случае, ни "Пётр" ни "Владислав" не
          войдут в результат сопоставления.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code>(?&#x3C;!<em>y</em>)<em>x</em></code>
      </td>
      <td>
        <table>
          <tbody>
            <tr>
              <td>
                <p>
                  <code
                    ><font face="Arial, x-locale-body, sans-serif"
                      ><span style="background-color: #ffffff"
                        >Сопоставляется с
                      </span></font
                    ><em>x</em></code
                  >, только если <code><em>x</em></code> не предшествует
                  <code><em>y</em></code>
                </p>
                <p>
                  Например, <code>/(?&#x3C;!-)\d+/</code> сопоставится с цифрой,
                  только если ей не предшествует минус.<br /><code
                    >/(?&#x3C;!-)\d+/.exec('3')</code
                  >
                  вернёт "3".<br /><code>/(?&#x3C;!-)\d+/.exec('-3')</code> не
                  сопоставится с цифрой, тк цифре перед цифрой 3 присутствует
                  минус.
                </p>
              </td>
            </tr>
          </tbody>
        </table>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>|<em>y</em></code>
      </td>
      <td>
        <p>
          Сопоставляется либо с <code><em>x</em></code
          >, либо с <code><em>y</em></code
          >.
        </p>
        <p>
          Например, шаблон <code>/зелёное|красное/</code> сопоставится с
          подстрокой «зелёное» в строке «зелёное яблоко» и подстрокой «красное»
          в строке «красное яблоко».
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>{<em>n</em>}</code>
      </td>
      <td>
        <p>
          Где <code><em>n</em></code> является целым положительным числом.
          Сопоставляется точно с <code><em>n</em></code> вхождениями
          предшествующего элемента <em>x</em>.
        </p>
        <p>
          Например, шаблон <code>/о{2}/</code> не сопоставится с символом «о» в
          слове «конфета», но сопоставится со всеми символами «о» в слове
          «коонфета» и с первыми двумя символами «о» в слове «кооонфета».
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>{<em>n</em>,}</code>
      </td>
      <td>
        <p>
          Где <code><em>n</em></code> является целым положительным числом.
          Сопоставляется по крайней мере с <code><em>n</em></code> вхождениями
          предшествующего элемента <em>x</em>.
        </p>
        <p>
          Например, шаблон <code>/о{2,}/</code> не сопоставится с символом «о» в
          слове «конфета», но сопоставится со всеми символами «о» в словах
          «коонфета» и даже в «кооооооонфета».
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <code><em>x</em>{<em>n</em>,<em>m</em>}</code>
      </td>
      <td>
        <p>
          Где <code><em>n</em></code> и <code><em>m</em></code> являются целыми
          положительными числами. Сопоставляется по крайней мере с
          <code><em>n</em></code> но не более, чем с
          <code><em>m</em></code> вхождениями предшествующего элемента
          <em>x</em>.
        </p>
        <p>
          Например, шаблон <code>/о{1,3}/</code> ни с чем не сопоставится в
          слове «кнфета», с символом «о» в слове «конфета», с двумя символами
          «о» в слове «коонфета» и с первыми тремя символами «о» в слове
          «кооооооонфета». Обратите внимание, что при сопоставлении со словом
          «кооооооонфета» сопоставимость только подстрока «ооо», хотя слово
          содержало гораздо больше символов «о».
        </p>
      </td>
    </tr>
  </tbody>
</table>

## Свойства

- {{jsxref("RegExp.prototype")}}
  - : Позволяет добавлять свойства ко всем объектам регулярных выражений.
- `RegExp.length`
  - : Значение `RegExp.length` равно 2.

## Методы

Глобальный объект `RegExp` не имеет собственных методов, однако, он наследует некоторые методы через цепочку прототипов.

## Экземпляры регулярного выражения

### Свойства

{{page('/ru/docs/Web/JavaScript/Reference/Global_Objects/RegExp/prototype', 'Properties')}}

### Методы

{{page('/ru/docs/Web/JavaScript/Reference/Global_Objects/RegExp/prototype', 'Methods')}}

## Примеры

### Пример: использование регулярных выражений для смены формата данных

Следующий скрипт использует метод {{jsxref("String.prototype.replace()", "replace()")}} экземпляра строки {{jsxref("Global_Objects/String", "String")}} для сопоставления с именем в формате _имя фамилия_ и выводит его в формате _фамилия, имя_. В тесте замены скрипт использует заменители `$1` и `$2`, которые заменяются на результаты соответствующих сопоставившихся подгрупп регулярного выражения.

```js
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1");
console.log(newstr);

// пример с русскими буквами
var re = /([а-яё]+)\s([а-яё]+)/i;
var str = "Джон Смит";
var newstr = str.replace(re, "$2, $1");
console.log(newstr);
```

Пример выведет «Smith, John» и «Смит, Джон»

### Пример: использование регулярного выражения для разбиения строк с различными символами конца строки

Символы конца строки различаются на различных платформах (Unix, Windows и так далее). Разбиение строк из этого примера работает на всех платформах.

```js
var text = "Некоторый текст\nЕщё текст\r\nИ ещё\rЭто конец";
var lines = text.split(/\r\n|\r|\n/);
console.log(lines); // выведет [ 'Некоторый текст', 'Ещё текст', 'И ещё', 'Это конец' ]
```

Обратите внимание, что порядок шаблонов в регулярном выражении имеет значение.

### Пример: использование регулярных выражений на нескольких строках

```js
var s = "Please yes\nmake my day!";
s.match(/yes.*day/);
// Вернёт null
s.match(/yes[^]*day/);
// Вернёт 'yes\nmake my day'
```

### Пример: использование регулярных выражений с флагом «липучести»

Этот пример демонстрирует, как можно использовать флаг «липучести» регулярных выражений для сопоставления с отдельными строками многострочного ввода.

```js
var text = "Первая строка\nВторая строка";
var regex = /(\S+) строка\n?/y;

var match = regex.exec(text);
console.log(match[1]); // напечатает 'Первая'
console.log(regex.lastIndex); // напечатает '14'

var match2 = regex.exec(text);
console.log(match2[1]); // напечатает 'Вторая'
console.log(regex.lastIndex); // напечатает '27'

var match3 = regex.exec(text);
console.log(match3 === null); // напечатает 'true'
```

Во время выполнения можно проверить, поддерживается ли флаг «липучести», при помощи блока `try { … } catch { … }`. Для этого надо использовать либо выражение с `eval(…)`, либо конструктор `RegExp(строка-регулярки, строка-с-флагами)` (поскольку нотация `/регулярка/флаги` обрабатывается во время компиляции, исключение будет выброшено до того, как выполнение достигнет блока `catch`). Например:

```js
var supports_sticky;
try {
  RegExp("", "y");
  supports_sticky = true;
} catch (e) {
  supports_sticky = false;
}
console.log(supports_sticky); // напечатает 'true'
```

### Пример: регулярные выражения и символы Юникода

Как уже сказано выше, символьные классы `\w` и `\W` сопоставляются только с базовыми символами ASCII; то есть, с символами от «a» до «z», от «A» до «Z», от «0» до «9» и символом «\_». Для сопоставления с символами из других языков, например, с кириллическими или иврита, используйте форму `\uhhhh`, где «hhhh» — это значение символа Юникода, записанное в шестнадцатеричной форме. Этот пример демонстрирует, как можно выделить символы Юникода, составляющие слова.

```js
var text = "Образец text на русском языке";
var regex = /[\u0400-\u04FF]+/g;

var match = regex.exec(text);
console.log(match[0]); // напечатает 'Образец'
console.log(regex.lastIndex); // напечатает '7'

var match2 = regex.exec(text);
console.log(match2[0]); // напечатает 'на' [не 'text']
console.log(regex.lastIndex); // напечатает '15'

// и так далее
```

Вот на этом внешнем ресурсе можно составить полный диапазон блоков Юникода для различных письменностей: [regexp-unicode-block](http://kourge.net/projects/regexp-unicode-block).

### Пример: извлечение имени поддомена из URL

```js
var url = "http://xxx.domain.com";
console.log(/[^.]+/.exec(url)[0].substr(7)); // напечатает 'xxx'
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

### Примечания по Gecko

Начиная с Gecko 34, в случае захвата группы с квантификаторами, предотвращающими появление группы в результате сопоставления, сопоставившийся текст для захваченной группы теперь имеет значение `undefined` вместо пустой строки:

```js
// Firefox 33 или более ранние
"x".replace(/x(.)?/g, function (m, group) {
  console.log("'group:" + group + "'");
}); // 'group:'

// Firefox 34 или более новые
"x".replace(/x(.)?/g, function (m, group) {
  console.log("'group:" + group + "'");
}); // 'group:undefined'
```

Обратите внимание, что для поддержания обратной совместимости, свойства `RegExp.$N` по-прежнему возвращают пустую строку вместо значения `undefined` ([bug 1053944](https://bugzilla.mozilla.org/show_bug.cgi?id=1053944)).

## Смотрите также

- Глава про [регулярные выражения](/ru/docs/Web/JavaScript/Guide/Regular_Expressions) в [руководстве по JavaScript](/ru/docs/Web/JavaScript/Guide)
- {{jsxref("String.prototype.match()")}}
- {{jsxref("String.prototype.replace()")}}