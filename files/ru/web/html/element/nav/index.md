---
title: <nav> - элемент навигации
slug: Web/HTML/Element/nav
---

**HTML-элемент `<nav>`** определяет отдельную секцию документа, назначение которой обозначение ссылок навигации (как внутри текущего документа, так и ведущих на другую страницу). В качестве примера такой секции можно привести меню, якорные ссылки.

| [Категории контента](/ru/docs/Web/Guide/HTML/Content_categories) | Потоковый контент, секционный контент, явный контент. |
| ---------------------------------------------------------------- | ----------------------------------------------------- |
| Допустимое содержимое                                            | Потоковый контент.                                    |
| Пропуск тегов                                                    | {{no_tag_omission}}                                   |
| Допустимые родители                                              | Любой элемент, содержащий потоковый контент.          |
| Допустимые ARIA-роли                                             | Нет                                                   |
| DOM-интерфейс                                                    | {{domxref("HTMLElement")}}                            |

## Атрибуты

Этот элемент поддерживает [глобальные атрибуты](/ru/docs/Web/HTML/%D0%9E%D0%B1%D1%89%D0%B8%D0%B5_%D0%B0%D1%82%D1%80%D0%B8%D0%B1%D1%83%D1%82%D1%8B).

## Примечание

- Не обязательно все ссылки должны быть обёрнуты в `<nav>`. `<nav>` следует использовать лишь для главных навигационных блоков. Например, {{HTMLElement("footer")}} часто содержит список ссылок, которые не стоит оборачивать в {{HTMLElement("nav")}} .
- Документ может содержать несколько {{HTMLElement("nav")}} элементов. Например, один для навигации по сайту, второй для навигации по странице.
- Пользовательские агенты, такие как устройства чтения с экрана, предназначенные для людей с плохим зрением, могут использовать этот элемент, чтобы определить следует ли пускать рендеринг содержимого навигации.

## Примеры

В данном примере, блок `<nav>` содержит ненумерованный список ({{HTMLElement("ul")}}) ссылок. С помощью CSS данный блок можно использовать как сайдбар, навигационную колонку или выпадающее меню.

```html
<nav class="menu">
  <ul>
    <li><a href="#">Главная</a></li>
    <li><a href="#">О нас</a></li>
    <li><a href="#">Контакты</a></li>
  </ul>
</nav>
```

## Спецификация

{{Specifications}}

## Совместимость браузера

{{Compat}}

## Смотрите также

- Другие секционные элементы: {{HTMLElement("body")}}, {{HTMLElement("article")}}, {{HTMLElement("section")}}, {{HTMLElement("aside")}}, {{HTMLElement("h1")}}, {{HTMLElement("h2")}}, {{HTMLElement("h3")}}, {{HTMLElement("h4")}}, {{HTMLElement("h5")}}, {{HTMLElement("h6")}}, {{HTMLElement("hgroup")}}, {{HTMLElement("header")}}, {{HTMLElement("footer")}}, {{HTMLElement("address")}};
- [Разделы и структура документа HTML5](/ru/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document).