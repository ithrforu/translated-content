---
title: <body>
slug: Web/HTML/Element/body
---

{{HTMLSidebar}}

**HTML-элемент `<body>`** представляет собой контент (содержимое) документа HTML. В документе может быть только один элемент `<body>`.

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/ru/docs/Web/Guide/HTML/Content_categories"
          >Категории контента</a
        >
      </th>
      <td>
        <a
          href="/ru/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document#Корни_задания_разделов"
          >Секционный корень</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Допустимое содержимое</th>
      <td>
        <a href="/ru/docs/Web/Guide/HTML/Content_categories#Потоковый_контент"
          >Потоковый контент</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Пропуск тегов</th>
      <td>
        Открывающий тег может быть пропущен, если первое, что находится внутри
        него, не является пробелом, комментарием, элементом
        {{HTMLElement("script")}} или элементом
        {{HTMLElement("style")}}. Закрывающий тег может быть пропущен
        если элемент <code>&#x3C;body></code> содержит контент или имеет
        открывающий тег, и за ним сразу не следует комментарий.
      </td>
    </tr>
    <tr>
      <th scope="row">Допустимые родители</th>
      <td>
        Этот элемент должен быть вторым в элементе
        {{HTMLElement("html")}}
      </td>
    </tr>
    <tr>
      <th scope="row">Допустимые ARIA-роли</th>
      <td>Отсутствуют</td>
    </tr>
    <tr>
      <th scope="row">DOM-интерфейс</th>
      <td>
        {{domxref("HTMLBodyElement")}}
        <ul>
          <li>
            Элемент <code>&#x3C;body></code> представляет интерфейс
            {{domxref("HTMLBodyElement")}}.
          </li>
          <li>
            Вы можете получить доступ к элементу <code>&#x3C;body></code> через
            свойство {{domxref("document.body")}}.
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Атрибуты

К этому элементу применимы [глобальные атрибуты](/ru/docs/Web/HTML/Общие_атрибуты).

- {{htmlattrdef("alink")}}
  - : Цвет текста гиперссылок, когда они выделены. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("color")}} вместе с псевдоклассом {{cssxref(":active")}}._
- {{htmlattrdef("background")}}
  - : URI изображения для использования в качестве фона. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("background")}}._
- {{htmlattrdef("bgcolor")}}
  - : Цвет фона документа. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("background-color")}}._
- {{htmlattrdef("bottommargin")}}
  - : Отступ от нижнего края элемента `<body>`. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("margin-bottom")}}._
- {{htmlattrdef("leftmargin")}}
  - : Отступ от левого края элемента `<body>`. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("margin-left")}}._
- {{htmlattrdef("link")}}
  - : Цвет текста непосещенных гипертекстовых ссылок. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("color")}} вместе с псевдоклассом {{cssxref(":link")}}._
- {{htmlattrdef("onafterprint")}}
  - : Функция для вызова после того, как пользователь распечатал документ.
- {{htmlattrdef("onbeforeprint")}}
  - : Функция для вызова, когда пользователь отправляет документ на печать.
- {{htmlattrdef("onbeforeunload")}}
  - : Функция для вызова перед закрытием окна документа или переходом на другую, внешнюю, страницу в этой же вкладке.
- {{htmlattrdef("onblur")}}
  - : Функция для вызова при потери документом фокуса.
- {{htmlattrdef("onerror")}}
  - : Функция для вызова, когда документ не загружается должным образом.
- {{htmlattrdef("onfocus")}}
  - : Функция для вызова, когда документ получает фокус.
- {{htmlattrdef("onhashchange")}}
  - : Функция для вызова, когда изменяется часть идентификатора фрагмента (начинается с символа `'#'`) текущего адреса документа.
- {{htmlattrdef("onlanguagechange")}} {{experimental_inline}}
  - : Функция для вызова при изменении предпочитаемых языков.
- {{htmlattrdef("onload")}}
  - : Функция для вызова, когда документ закончил загрузку (страницы загружена).
- {{htmlattrdef("onmessage")}}
  - : Функция для вызова, когда документ получил сообщение.
- {{htmlattrdef("onoffline")}}
  - : Функция для вызова, когда происходит сбой сетевого соединения.
- {{htmlattrdef("ononline")}}
  - : Функция для вызова, когда произошло восстановление сетевого соединения.
- {{htmlattrdef("onpopstate")}}
  - : Функция для вызова, когда пользователь осуществил управление историей сеанса.
- {{htmlattrdef("onredo")}}
  - : Функция для вызова, когда произошло продвижение пользователя вперёд по истории транзакций (например, обновление страницы).
- {{htmlattrdef("onresize")}}
  - : Функция для вызова, когда размер документа был изменён.
- {{htmlattrdef("onstorage")}}
  - : Функция для вызова, когда изменяется содержимое хранилища ([Web Storage](/ru/docs/Web/API/Web_Storage_API)).
- {{htmlattrdef("onundo")}}
  - : Функция для вызова, когда произошло продвижение пользователя назад по истории транзакций (например, переход на предыдущую страницу в активной вкладке).
- {{htmlattrdef("onunload")}}
  - : Функция для вызова, когда пользователь покидает страницу (закрытие вкладки или окна браузера).
- {{htmlattrdef("rightmargin")}}
  - : Отступ от правого края элемента `<body>`. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("margin-right")}}._
- {{htmlattrdef("text")}}
  - : Основной цвет текста. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("color")}}._
- {{htmlattrdef("topmargin")}}
  - : Отступ от верхнего края элемента `<body>`. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("margin-top")}}._
- {{htmlattrdef("vlink")}}
  - : Цвет текста посещённой гипертекстовой ссылки. _Этот метод не согласован, вместо него используйте CSS-свойство {{cssxref("color")}} вместе с псевдоклассом {{cssxref(":visited")}}._

## Пример

```html
<html>
  <head>
    <title>Заголовок документа</title>
  </head>
  <body>
    <p>Это параграф</p>
  </body>
</html>
```

## Спецификации

{{Specifications}}

## Поддержка браузерами

{{Compat}}

## Смотрите также

- {{HTMLElement("html")}}
- {{HTMLElement("head")}}