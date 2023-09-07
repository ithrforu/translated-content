---
title: CSS-селекторы
slug: Web/CSS/CSS_selectors
---

{{CSSRef}}

**Селектор** определяет, к какому элементу применять то или иное CSS-правило.

Обратите внимание - не существует селекторов, которые бы позволили выбрать родителя (содержащий контейнер) или соседа родителя или потомков соседа родителя.

## Базовые селекторы

- [Универсальный селектор](/ru/docs/Web/CSS/Universal_selectors)

  - : Выбирает все элементы. По желанию, он может быть ограничен определённым пространством имён или относиться ко всему пространству имён.

    **Синтаксис:** `*` `ns|*` `*|*`

    **Пример:** `*` будет соответствовать всем элементам на странице.

- [Селекторы по типу элемента](/ru/docs/Web/CSS/Type_selectors)

  - : Этот базовый селектор выбирает тип элементов, к которым будет применяться правило.

    **Синтаксис:** `элемент`

    **Пример:** селектор `input` выберет все элементы {{HTMLElement('input')}}.

- [Селекторы по классу](/ru/docs/Web/CSS/Class_selectors)

  - : Этот базовый селектор выбирает элементы, основываясь на значении их атрибута `class`.

    **Синтаксис:** `.имяКласса`

    **Пример:** селектор `.index` выберет все элементы с соответствующим классом (который был определён в атрибуте `class="index"`).

- [Селекторы по идентификатору](/ru/docs/Web/CSS/ID_selectors)

  - : Этот базовый селектор выбирает элементы, основываясь на значении их `id` атрибута. Не забывайте, что идентификатор должен быть уникальным, т. е. использоваться только для одного элемента в HTML-документе.

    **Синтаксис:** `#имяИдентификатора`

    **Пример:** селектор `#toc` выберет элемент с идентификатором toc (который был определён в атрибуте `id="toc"`).

- [Селекторы по атрибуту](/ru/docs/Web/CSS/Attribute_selectors)

  - : Этот селектор выбирает все элементы, имеющие данный атрибут или атрибут с определённым значением.

    **Синтаксис:** `[attr] [attr=value] [attr~=value] [attr|=value] [attr^=value] [attr$=value] [attr*=value]`

    **Пример:** селектор `[autoplay]` выберет все элементы, у которых есть атрибут `autoplay` (независимо от его значения).

    **Ещё пример**: a\[href$=".jpg"] выберет все ссылки, у которых адрес заканчивается на ".jpg".

    **Ещё пример**: a\[href^="https"] выберет все ссылки, у которых адрес начинается на "https".

## Комбинаторы

- [Комбинатор запятая](/ru/docs/Web/CSS/Comma_combinator)

  - : Комбинатор `,` это способ группировки, он выбирает все совпадающие узлы.

    **Синтаксис:** `A, B`

    **Пример:** `div, span` выберет оба элемента - и {{HTMLElement("div")}} и {{HTMLElement("span")}}.

- [Комбинатор потомков](/ru/docs/Web/CSS/Descendant_selectors)

  - : Комбинатор `' '` (пробел) выбирает элементы, которые находятся внутри указанного элемента (вне зависимости от уровня вложенности).

    **Синтаксис:** `A B`

    **Пример:** селектор `div span` выберет все элементы {{HTMLElement('span')}}, которые находятся внутри элемента {{HTMLElement('div')}}.

- [Дочерние селекторы](/ru/docs/Web/CSS/Child_selectors)

  - : Комбинатор `'>'` в отличие от пробела выбирает только те элементы, которые являются дочерними непосредственно по отношению к указанному элементу.

    **Синтаксис:** `A > B`

    **Пример:** селектор `ul > li` выберет только дочерние элементы {{HTMLElement('li')}}, которые находятся внутри, на первом уровне вложенности по отношению к элементу {{HTMLElement('ul')}}.

- [Комбинатор всех соседних элементов](/ru/docs/Web/CSS/General_sibling_selectors)

  - : Комбинатор `'~'` выбирает элементы, которые находятся на этом же уровне вложенности, после указанного элемента, с тем же родителем.

    **Синтаксис:** `A ~ B`

    **Пример:** `p ~ span` выберет все элементы {{HTMLElement('span')}}, которые находятся после элемента {{HTMLElement('p')}} внутри одного родителя.

- [Комбинатор следующего соседнего элемента](/ru/docs/Web/CSS/Adjacent_sibling_selectors)

  - : Комбинатор `'+'` выбирает элемент, который находится непосредственно после указанного элемента, если у них общий родитель.

    **Синтаксис:** `A + B`

    **Пример:** селектор `h2 + p` выберет первый элемент {{HTMLElement("p")}}, который находится _непосредственно_ после элемента {{HTMLElement("h2")}}.

## Псевдо

- [Псевдоклассы](/ru/docs/Web/CSS/Pseudo-classes)

  - : Знак `:` позволяет выбрать элементы, основываясь на информации, которой нет в дереве элементов.

    **Пример:** `a:visited` соответствует всем элементам {{HTMLElement("a")}} которые имеют статус "посещённые".

    **Ещё пример**: `div:hover` соответствует элементу, над которым проходит указатель мыши.

    **Ещё пример**: `input:focus` соответствует полю ввода, которое получило фокус.

- [Псевдоэлементы](/ru/docs/Web/CSS/Pseudo-elements)

  - : Знак `::` позволяет выбрать вещи, которых нет в HTML.

    **Пример:** `p::first-line` соответствует первой линии абзаца {{HTMLElement("p")}}.

## Версии CSS

| Спецификация                            | Статус                      | Комментарии                                                                                                                                                                                                                                                                                                        |
| --------------------------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| {{SpecName('CSS4 Selectors')}}          | {{Spec2('CSS4 Selectors')}} | Добавление комбинатора колонок `\|\|` , селекторов структуры сеточной разметки (CSS grid selector), логических комбинаторов, местоположения, временных, состояния ресурсов, лингвистических и UI псевдоклассов, модификаторов для ASCII регистрозависимых и регистронезависимых атрибутов со значениями и без них. |
| {{SpecName('CSS3 Selectors')}}          | {{Spec2('CSS3 Selectors')}} | Добавлен комбинатор `~` и древовидные структурные псевдоклассы. Сделаны псевдоэлементы, использующие префикс `::` двойное двоеточие. Селекторы дополнительных атрибутов.                                                                                                                                           |
| {{SpecName('CSS2.1', 'selector.html')}} | {{Spec2('CSS2.1')}}         | Добавлен комбинатор потомков `>` и комбинатор следующего соседа `+` . Добавлен **универсальный (\*)** комбинатор и **селектор атрибутов.**                                                                                                                                                                         |
| {{SpecName('CSS1')}}                    | {{Spec2('CSS1')}}           | Первоначальное определение.                                                                                                                                                                                                                                                                                        |

## Смотрите также

[CSS специфичность](/ru/docs/Web/CSS/Specificity)