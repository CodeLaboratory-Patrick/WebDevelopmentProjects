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
## ⭐️ Understanding HTML Nesting and Indentation

## Introduction  
One of the key principles of writing clean, maintainable HTML code is **nesting** and **indentation**. Nesting places elements within other elements in a structured, hierarchical manner. Indentation visually aligns these elements to communicate the document’s structure clearly.

## What is Nesting in HTML?  
Nesting in HTML refers to placing one element inside another to build a hierarchical structure.

### Key Characteristics of Nesting  
1. **Parent-Child Relationship**  
   - The outer element is called the *parent*, while the inner element is called the *child*.  
   - **Example**:  
     ```html
     <div>
         <p>This paragraph is nested inside the div.</p>
     </div>
     ```

2. **Semantic Structure**  
   - Properly nested elements help define document structure for browsers, screen readers, and search engines.

3. **HTML Validation**  
   - Incorrect nesting can break layout and fail validation.  
   - **Example of Incorrect Nesting**:  
     ```html
     <p>
         This is incorrect nesting.
         <div>Div is opened inside p.</p>
     </div>
     ```

## What is Indentation in HTML?  
Indentation is adding consistent spaces or tabs before nested elements so developers can quickly identify the hierarchy.

### Key Characteristics of Indentation  
1. **Readability**  
   - Properly indented code is easier to understand at a glance.

2. **Consistent Style**  
   - Decide on a standard indentation (e.g., 2 spaces, 4 spaces, or tabs) to maintain consistency.

3. **Common Patterns**  
   - 2 or 4 spaces for each level of nesting.  
   - **Example**:  
     ```html
     <nav>
         <ul>
             <li><a href="#">Home</a></li>
             <li><a href="#">About</a></li>
             <li><a href="#">Contact</a></li>
         </ul>
     </nav>
     ```

## Examples of Nesting and Indentation  

### Example 1: Basic Nesting Structure  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nested Elements Example</title>
</head>
<body>
    <main>
        <section>
            <h1>Main Heading</h1>
            <p>This paragraph is nested inside a section.</p>
        </section>
    </main>
</body>
</html>
```
- `<section>` is nested inside `<main>`.  
- `<h1>` and `<p>` are nested inside `<section>`.

### Example 2: Nested Lists  
```html
<ul>
    <li>Item One
        <ul>
            <li>Subitem One</li>
            <li>Subitem Two</li>
        </ul>
    </li>
    <li>Item Two</li>
</ul>
```
- The second `<ul>` is nested inside the first list’s `<li>`.

### Example 3: Incorrect vs. Correct Nesting  

**Incorrect Nesting**:  
```html
<p>
    <strong>This is strong text.
</p>
</strong>
```

**Correct Nesting**:  
```html
<p>
    <strong>This is strong text.</strong>
</p>
```

## Comparison Table: Poor vs. Good Nesting and Indentation  
| Style                 | Characteristics                                                          | Example                             |
|-----------------------|--------------------------------------------------------------------------|-------------------------------------|
| **Poor Nesting**      | Elements are out of order, missing, or mismatched closing tags           | `<p><strong>Text</p></strong>`      |
| **Poor Indentation**  | Inconsistent spacing, everything on one line, or random alignment         | `<div><p>Text</p></div>` (all inline) |
| **Good Nesting**      | Properly ordered parent-child relationships, every element is closed      | `<p><strong>Text</strong></p>`      |
| **Good Indentation**  | Consistent indentation that visually reflects nested structure            | 2 or 4 spaces for each nested level |

## Visual Diagram  
```plaintext
<html>
├── <head>
│     └── <meta>
└── <body>
      ├── <header>
      ├── <main>
      │     └── <section>
      │           ├── <h1>
      │           └── <p>
      └── <footer>
```
The diagram shows a typical hierarchical structure. Notice how each nested element is visually indented under its parent.

## References  
1. [MDN Web Docs - HTML Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics)  
2. [W3Schools - HTML Elements](https://www.w3schools.com/html/html_elements.asp)  
3. [HTML Living Standard](https://html.spec.whatwg.org/)

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 



