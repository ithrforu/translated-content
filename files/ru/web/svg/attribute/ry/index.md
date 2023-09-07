---
title: ry
slug: Web/SVG/Attribute/ry
---

{{SVGRef}}

Атрибут **`ry`** определяет радиус круга по оси y.

Два элемента используют этот атрибут: [`<ellipse>`](/ru/docs/Web/SVG/Element/ellipse) и [`<rect>`](/ru/docs/Web/SVG/Element/rect)

```css hidden
html,
body,
svg {
  height: 100%;
}
```

```html
<svg viewBox="0 0 300 200" xmlns="http://www.w3.org/2000/svg">
  <ellipse cx="50" cy="50" ry="0" rx="25" />
  <ellipse cx="150" cy="50" ry="25" rx="25" />
  <ellipse cx="250" cy="50" ry="50" rx="25" />

  <rect x="20" y="120" width="60" height="60" ry="0" rx="15" />
  <rect x="120" y="120" width="60" height="60" ry="15" rx="15" />
  <rect x="220" y="120" width="60" height="60" ry="150" rx="15" />
</svg>
```

{{EmbedLiveSample('topExample', '100%', 200)}}

## ellipse

Для элемента {{SVGElement('ellipse')}}, `ry` определяет радиус фигуры по оси y. Если значение меньше или равно 0, эллипс не будет нарисован вообще.

| Значение              | **[\<length>](/docs/Web/SVG/Content_type#Length)** \| **[\<percentage>](/docs/Web/SVG/Content_type#Percentage)** \| `auto` |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Значение по умолчанию | `auto`                                                                                                                     |
| Анимируемый           | Да                                                                                                                         |

> **Примечание:** Начиная с **SVG2**, **ry** - _свойство геометрии(Geometry Property)._ Это означает, что атрибут также можно использовать как свойство CSS для эллипсов.

## rect

Для {{SVGElement('rect')}}, `ry` определяет радиус эллипса по оси x, используется для скругления углов прямоугольника.

Способ интерпретации значения атрибута `ry` зависит как от атрибута {{SVGAttr("rx")}} , так и от ширины прямоугольника:

- Если правильно задано значение для `ry`, но не для {{SVGAttr("rx")}} (или наоборот), то браузер сочтёт отсутствующее значение равным указанному.
- Если ни `ry`, ни {{SVGAttr("rx")}} не имеют правильно указанного значения, браузер нарисует прямоугольник с квадратными углами.
- Если `ry` больше половины ширины прямоугольника, то браузер будет считать значение `ry` половиной ширины прямоугольника.

| Значение              | **[\<length>](/docs/Web/SVG/Content_type#Length)** \| **[\<percentage>](/docs/Web/SVG/Content_type#Percentage)** \| `auto` |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Значение по умолчанию | `auto`                                                                                                                     |
| Анимируемый           | Да                                                                                                                         |

> **Примечание:** Начиная с **SVG2**, **ry** - _свойство геометрии(Geometry Property)._ Это означает, что атрибут также можно использовать как свойство CSS для rect.

## Specifications

| Спецификация                                                          | Статус              | Комментарий                           |
| --------------------------------------------------------------------- | ------------------- | ------------------------------------- |
| {{SpecName("SVG2", "geometry.html#RY", "ry")}}                        | {{Spec2("SVG2")}}   | Определяется как свойство геометрии   |
| {{SpecName("SVG1.1", "shapes.html#EllipseElementRYAttribute", "ry")}} | {{Spec2("SVG1.1")}} | Начальное определение для `<ellipse>` |
| {{SpecName("SVG1.1", "shapes.html#RectElementRYAttribute", "ry")}}    | {{Spec2("SVG1.1")}} | Начальное определение для `<rect>`    |