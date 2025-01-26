# Intermediate HTML

---
## ⭐️ HTML Unordered List, Ordered List, and List Item

## Introduction
HTML lists are used to group related items. They play a vital role in structuring information logically and clearly. The three main elements for creating lists are:

1. `<ul>`: Defines an **unordered** list
2. `<ol>`: Defines an **ordered** list
3. `<li>`: Defines a **list item**

## What Are Unordered and Ordered Lists?
### Unordered List (`<ul>`)
- **Definition**: An unordered list is a collection of items marked with bullets (●) or other custom symbols.
- **Syntax**:
  ```html
  <ul>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
  </ul>
  ```
- **Default Marker**: A solid round bullet.
- **Use Cases**: Used when the order of items does not matter, such as listing ingredients in a recipe, or enumerating features of a product.

### Ordered List (`<ol>`)
- **Definition**: An ordered list is a collection of items marked with numbers, letters, or Roman numerals.
- **Syntax**:
  ```html
  <ol>
      <li>First Item</li>
      <li>Second Item</li>
      <li>Third Item</li>
  </ol>
  ```
- **Default Marker**: Sequential numbers (1, 2, 3, ...).
- **Attributes**:
  - `type`: Specifies the marker type (e.g., `type="A"` for uppercase letters, `type="a"` for lowercase letters, `type="I"` for Roman numerals, etc.).
  - `start`: Specifies the starting value of the list (e.g., `start="5"`).
- **Use Cases**: Used when the order of items is important, such as steps in a procedure or instructions.

### List Item (`<li>`)
- **Definition**: Represents a single item within either an unordered or ordered list.
- **Characteristics**:
  - Can contain text, inline elements, and block-level elements.
  - Typically placed inside `<ul>` or `<ol>`.

## Examples

### 1. Unordered List Example
```html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```
**Output**:
- HTML
- CSS
- JavaScript

### 2. Ordered List with Attributes
```html
<ol type="I" start="4">
    <li>Step One</li>
    <li>Step Two</li>
    <li>Step Three</li>
</ol>
```
**Output**:
IV. Step One
V. Step Two
VI. Step Three

### 3. Nested Lists
```html
<ul>
    <li>Frontend
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </li>
    <li>Backend
        <ol>
            <li>Node.js</li>
            <li>Python</li>
            <li>Java</li>
        </ol>
    </li>
</ul>
```
**Structure**:
- Frontend
  - HTML
  - CSS
  - JavaScript
- Backend
  1. Node.js
  2. Python
  3. Java

## Styling Lists with CSS
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Styled Lists</title>
    <style>
        ul.custom-bullet {
            list-style-type: square;
        }
        ol.custom-order {
            list-style-type: upper-alpha;
        }
    </style>
</head>
<body>
    <ul class="custom-bullet">
        <li>List item A</li>
        <li>List item B</li>
    </ul>

    <ol class="custom-order">
        <li>Ordered item A</li>
        <li>Ordered item B</li>
    </ol>
</body>
</html>
```
**Notes**:
- `list-style-type` determines the type of bullet or numbering style.
- Other properties such as `padding` or `margin` can be applied to adjust spacing.

## Comparison Table
| List Type       | Element  | Default Marker       | Use Cases                            |
|-----------------|----------|----------------------|--------------------------------------|
| Unordered List  | `<ul>`   | Bullets (●)          | General grouping of items, order not important  |
| Ordered List    | `<ol>`   | Numbers (1, 2, 3...) | Steps, rankings, or procedures where order matters |
| List Item       | `<li>`   | Inherits from `<ul>` or `<ol>` | Represents an item in either list |

## Visual Diagram
Below is a diagram illustrating how lists nest with `<li>`:

```plaintext
<ol>
    ├── <li>First</li>
    ├── <li>Second</li>
    └── <li>Third
        └── <ul>
            ├── <li>Nested One</li>
            └── <li>Nested Two</li>
        </ul>
    </li>
</ol>
```

## References
1. [MDN Web Docs - `<ul>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul)
2. [MDN Web Docs - `<ol>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol)
3. [MDN Web Docs - `<li>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/li)
4. [W3Schools - HTML Lists](https://www.w3schools.com/html/html_lists.asp)
5. [HTML Living Standard](https://html.spec.whatwg.org/multipage/)

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 



