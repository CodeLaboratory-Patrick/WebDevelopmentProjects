# Advanced CSS

---
## ⭐️ Understanding the CSS Display Property

## Introduction
The `display` property in CSS defines how an element is displayed in the document layout. Whether you want to create inline elements that flow along text, block-level structures that take up full width, or inline-block elements that combine characteristics of both, the `display` property is crucial for fine-tuning layout behavior.

## Common Values for `display`
| Value         | Description                                                   | Typical Use Case                  |
|---------------|---------------------------------------------------------------|-----------------------------------|
| `block`       | Element is displayed as a **block**; occupies the full width, new line before/after | Paragraphs, divs, sections        |
| `inline`      | Element displays **inline**; no forced line breaks, width/height not modifiable | Text elements, `<span>`           |
| `inline-block`| Displays **inline** but allows setting width/height           | Buttons, images, advanced layout  |
| `none`        | Element is **not** displayed at all                           | Hiding elements                   |
| `flex`        | Establishes a **flex container** for flexible layouts         | Nav bars, responsive grids        |
| `grid`        | Establishes a **grid container** for 2D layouts              | Complex page layouts              |

## Other Display Values
| Value         | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `none`        | Element is removed from the layout (not rendered).                         |
| `flex`        | Enables flexible box layout (1D).                                           |
| `grid`        | Enables grid layout (2D).                                                   |
| `table`       | Behaves like a `<table>`.                                                   |
| `inline-flex` | Inline-level flex container.                                                |
| `inline-grid` | Inline-level grid container.                                                |

## Comparison Table
| Property       | Width Behavior       | Line Break | `width`/`height` | Vertical Margin/Padding |
|----------------|----------------------|------------|-------------------|-------------------------|
| `block`        | Full container width | Yes        | Yes               | Yes                     |
| `inline`       | Content width        | No         | No                | No (horizontal only)    |
| `inline-block` | Content/Explicit     | No         | Yes               | Yes                     |

### Additional Values
- `table`, `table-row`, `table-cell` (for table-like layouts)
- `list-item` (for custom bullet styling)

## Block-Level Elements (display: block)
1. **Full Width**: Stretches to fill its container.
2. **Starts on a New Line**: By default, a new line is placed before and after.
3. **Width/Height**: Customizable with CSS.
4. **Examples**: `<div>`, `<p>`, `<section>` (by default).

```css
.block-element {
  display: block;
  width: 80%;
  margin: 0 auto;
}
```

**Use Cases**:
- Creating major sections or containers.

## Inline Elements (display: inline)
1. **Flows with Text**: Occupies only its required width.
2. **Cannot** change `width` and `height` normally.
3. **Padding/Margin** affect horizontal spacing, but not vertical as expected.
4. **Examples**: `<span>`, `<a>`, `<strong>`.

```css
.inline-text {
  display: inline;
  background-color: yellow;
}
```

**Use Cases**:
- Highlighting words or small inline icons.

## Inline-Block Elements (display: inline-block)
1. **Inline** alignment but **block**-like properties.
2. **Width/Height** can be set.
3. **Vertical margins/padding** also respected.
4. Often used for **buttons**, **nav items**, or images.

```css
.inline-block-item {
  display: inline-block;
  width: 150px;
  height: 50px;
  background-color: #f0f0f0;
}
```

**Use Cases**:
- Creating horizontally aligned elements with specific sizes.

**Diagram**:
```plaintext
[ inline-block-1 ] [ inline-block-2 ] [ inline-block-3 ]
 Each item has its own set width/height while staying inline
```

## Display: none
1. The element **doesn’t render**; no space allocated.
2. Distinct from `visibility: hidden` (which hides element but keeps space).

```css
.hidden {
  display: none;
}
```

**Use Cases**:
- Temporarily removing an element from flow.
- Toggling UI components (e.g., dropdown menus) with JavaScript.

## Advanced Display Modes

### Flex
- Converts container into a **flex container**, enabling flexible layouts.
- Good for row or column-based distribution, alignment, spacing.

```css
.flex-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
```

### Grid
- Turns container into a **grid container**, ideal for 2D layouts.

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
```

## Table Display Properties
- `display: table`, `display: table-row`, `display: table-cell`.
- Mimics HTML table layout; can be used for older fallback layouts.

```css
.table-like {
  display: table;
  width: 100%;
}
.row-like {
  display: table-row;
}
.cell-like {
  display: table-cell;
}
```

**Use Cases**: Rare in modern layouts (Flex or Grid are more robust).

## Example Code Snippet
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Display Example</title>
  <style>
    .block-example {
      display: block;
      width: 50%;
      margin: 1rem auto;
      background-color: lightblue;
    }
    .inline-example {
      display: inline;
      background-color: pink;
      margin-right: 0.5rem;
    }
    .inline-block-example {
      display: inline-block;
      width: 100px;
      height: 100px;
      background-color: lightgreen;
      vertical-align: middle;
      margin: 0.5rem;
    }
  </style>
</head>
<body>
  <div class="block-example">This is a block element</div>

  <p>
    <span class="inline-example">Inline item 1</span>
    <span class="inline-example">Inline item 2</span>
  </p>

  <div>
    <div class="inline-block-example">Box 1</div>
    <div class="inline-block-example">Box 2</div>
    <div class="inline-block-example">Box 3</div>
  </div>
</body>
</html>
```

## References & Recommended Resources
1. [MDN Web Docs - `display`](https://developer.mozilla.org/en-US/docs/Web/CSS/display)
2. [CSS-Tricks - Display](https://css-tricks.com/almanac/properties/d/display/)
3. [W3Schools - CSS Display Property](https://www.w3schools.com/css/css_display_visibility.asp)

---
## ⭐️ Understanding CSS Float

## Introduction
The **float** property in CSS was originally designed to allow text to wrap around images, mimicking magazine-like layouts. Over time, developers began using float for entire page layouts before modern techniques (like Flexbox and Grid) became more common. While float-based layouts are less prevalent today, understanding floats remains essential for maintaining or refactoring older code and dealing with text-wrapping scenarios.

## How Does Float Work?
When an element is floated, it is **removed** from the normal document flow (to some extent) and shifted to the left or right side of its container. **Other inline content** (such as text or inline images) wraps around the floated element.

### Float Values
| Value   | Description                                           |
|---------|-------------------------------------------------------|
| `left`  | Floats the element to the left of the container       |
| `right` | Floats the element to the right of the container      |
| `none`  | Default; element does not float                       |
| `inherit` | Inherits the float property from its parent          |


### Example
```css
img {
  float: left;
  margin: 0 10px 10px 0; /* Creates space around the image */
}
```

This rule floats images to the left, allowing text to wrap on the right.

## Characteristics of Floated Elements
1. **Removed From Normal Flow**: Floated elements no longer occupy space in the normal layout, though they still affect surrounding inline content.
2. **Container Collapsing**: A parent container containing only floated elements can "collapse," having zero height. This often requires a "clearfix" solution to contain floats.
3. **Width**: Floated elements usually need an explicit width set, or they shrink to fit content.
4. **Clearing**: Sibling elements can use `clear` to prevent them from wrapping around a float.

## Float vs. Modern Layout Techniques
Floats were commonly used for **multi-column** layouts in older websites. Today:
- **Flexbox**: Better for one-dimensional layout (rows or columns), alignment, spacing.
- **Grid**: Ideal for two-dimensional or complex layouts.
- **Float**: Still valid for text wrapping around images, or legacy code maintenance.

**Advice**: For new designs, prefer flex or grid over float for major layout tasks.

## Common Float Issues and Solutions
### 1. Collapsing Containers
If a parent has only floated children, its height collapses. For example:
```html
<div class="float-container">
  <img src="image.jpg" alt="" style="float:left">
  <p>Some text that wraps around the floated image.</p>
</div>
```
Without extra measures, `.float-container` might have no height.

**Fix**:
- Use a **clearfix** hack or set `overflow`.

```css
.float-container {
  overflow: auto; /* or hidden */
}

/* or classic clearfix */
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

### 2. Clearing Floats
Use the `clear` property to prevent elements from flowing around a floated sibling.

```css
.clear-both {
  clear: both;
}
```

```html
<div style="float:left; width:200px;">Floating div</div>
<p class="clear-both">This paragraph starts below the float.</p>
```

### 3. Float Stacking
Multiple floated elements might stack incorrectly if widths aren’t properly set.

## Example Layout Using Float
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Float Layout Example</title>
<style>
  .container {
    width: 80%;
    margin: 0 auto;
    overflow: auto; /* prevents collapse */
    background-color: #f9f9f9;
  }
  .sidebar {
    float: left;
    width: 25%;
    background-color: lightblue;
  }
  .content {
    float: left;
    width: 75%;
    background-color: lightyellow;
  }
</style>
</head>
<body>
  <div class="container">
    <div class="sidebar">
      <h2>Sidebar</h2>
      <p>Some sidebar content</p>
    </div>
    <div class="content">
      <h1>Main Content</h1>
      <p>Lorem ipsum dolor sit amet...</p>
    </div>
  </div>
</body>
</html>
```
**Explanation**:
- Two columns: `.sidebar` floats left at 25%, `.content` floats left at 75%.
- `.container` uses `overflow:auto;` to contain floats.

## Diagram: Floating an Image
```plaintext
 +------------------------------------+
 | Here is some text that flows       |
 | around the floated image. The      |
 | image is on the left, text wraps   |
 | to the right, continuing down the  |
 | page.                              |
 +--floated-img--------+--------------+
 |  [Image content]    | Wrapping text|
 |                    | continues...  |
 +---------------------+--------------+
```

## References & Recommended Resources
1. [MDN Web Docs - float](https://developer.mozilla.org/en-US/docs/Web/CSS/float)
2. [CSS-Tricks - All About Floats](https://css-tricks.com/all-about-floats/)
3. [W3Schools - CSS Float](https://www.w3schools.com/css/css_float.asp)
4. [HTML Living Standard](https://html.spec.whatwg.org/)

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 

---
## ⭐️ 