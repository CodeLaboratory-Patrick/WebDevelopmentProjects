# CSS - Flexbox

---
## ⭐️ Understanding CSS Flexbox (`display: flex`)
## Introduction
**Flexbox** (short for **Flexible Box Layout**) is a modern CSS layout module that provides a more efficient way to align, distribute, and space elements within their container. Unlike traditional block or inline layouts, Flexbox is responsive by design, making it easier to create fluid and adaptive layouts for different screen sizes.

## Key Characteristics of Flexbox
1. **One-Dimensional Layout**: Focuses on arranging items in a single direction—either a row or a column.
2. **Flexible Sizing**: Items can shrink or grow based on available space and defined rules.
3. **Alignment & Spacing**: Provides powerful alignment options (e.g., centering, distribution) along the **main axis** and **cross axis**.
4. **Order Control**: Items can be visually reordered without changing the HTML structure.
5. **Responsive Friendly**: Simplifies building dynamic, adaptive layouts.

### Main and Cross Axes
Flexbox operates along two axes:
- **Main Axis**: Defined by `flex-direction` (default: horizontal).
- **Cross Axis**: Perpendicular to the main axis (default: vertical).

| `flex-direction` | Main Axis Direction | Cross Axis Direction |
|-------------------|---------------------|----------------------|
| `row` (default)   | Left to Right       | Top to Bottom        |
| `row-reverse`     | Right to Left       | Top to Bottom        |
| `column`          | Top to Bottom       | Left to Right        |
| `column-reverse`  | Bottom to Top       | Left to Right        |

## Basic Terminology
1. **Flex Container**: The parent element with `display: flex`.
2. **Flex Items**: Child elements directly inside the flex container.
3. **Main Axis**: The primary axis along which flex items are laid out (`flex-direction` defines if it’s horizontal or vertical).
4. **Cross Axis**: The perpendicular axis to the main axis.

**Diagram**:
```plaintext
Flex Container
┌───────────────────────────────────┐
| (main axis) -------------------->|
| [Item 1] [Item 2] [Item 3]       |  ← cross axis is vertical
└───────────────────────────────────┘
```

## Container Properties
### 1. `display: flex` or `inline-flex`
- Establishes a **flex container**.
- `inline-flex` creates an inline-level container rather than a block-level container.

### 2. `flex-direction`
- Determines if items are laid out in a **row** (horizontal) or **column** (vertical), and whether in reverse.

| Value      | Description                          |
|------------|--------------------------------------|
| `row`      | Horizontal, left-to-right (default)  |
| `row-reverse` | Horizontal, right-to-left         |
| `column`   | Vertical, top-to-bottom              |
| `column-reverse` | Vertical, bottom-to-top        |

### 3. `flex-wrap`
- Defines whether flex items can wrap onto multiple lines.

| Value      | Description                                  |
|------------|----------------------------------------------|
| `nowrap`   | All items stay on one line (default)         |
| `wrap`     | Items wrap to a new line if no space         |
| `wrap-reverse` | Wraps in reverse order                   |

### 4. `justify-content`
- Aligns items along the **main axis**.

| Value                | Description                                         |
|----------------------|-----------------------------------------------------|
| `flex-start`         | Items packed at the start of the main axis (default)|
| `flex-end`           | Items packed at the end of the main axis            |
| `center`             | Items centered along the main axis                  |
| `space-between`      | Equal space **between** items, none at edges        |
| `space-around`       | Equal space **around** items (edges included)       |
| `space-evenly`       | Equal space **between** items **and** edges         |

### 5. `align-items`
- Aligns items along the **cross axis**.

| Value         | Description                                              |
|---------------|----------------------------------------------------------|
| `stretch`     | Items stretch to fill the container (default)           |
| `flex-start`  | Items aligned to the start of the cross axis            |
| `flex-end`    | Items aligned to the end of the cross axis              |
| `center`      | Items centered on the cross axis                        |
| `baseline`    | Items aligned by their text baselines                   |

### 6. `align-content`
- Controls **extra space** on the cross axis when items wrap over multiple lines.
- Only works if multiple rows or columns exist (i.e., wrapping is enabled).
- Aligns lines within the container along the cross axis (for multi-line containers).
```css
.container {
  align-content: stretch | flex-start | flex-end | center | space-between | space-around;
}
```

### 7. `gap`, `column-gap`, `row-gap`
- Defines spacing between flex items. For example: `gap: 10px;`.
- Adds spacing between items.
```css
.container {
  gap: 10px; /* Spacing between items */
}
```

## Flex Item Properties
### 1. `flex: grow shrink basis;`
- A shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`.

**Example**:
```css
.item {
  flex: 1 1 200px;
}
```
- **flex-grow** (`1`): Item can grow if extra space is available.
- **flex-shrink** (`1`): Item can shrink if not enough space.
- **flex-basis** (`200px`): Initial size of the item before growing/shrinking.

### 2. `align-self`
- Overrides the `align-items` property for an individual flex item.

**Example**:
```css
.item {
  align-self: center;
}
```

### 3. `order`
- Changes the **visual order** of flex items without altering the source HTML.

**Example**:
```css
.item-1 {
  order: 2;
}
.item-2 {
  order: 1;
}
```

## Basic Example
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flexbox Example</title>
  <style>
    .container {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      border: 2px solid #333;
      padding: 10px;
    }

    .item {
      background-color: #f0f0f0;
      flex: 1 1 100px;
      text-align: center;
      padding: 20px;
      box-sizing: border-box;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
  </div>
</body>
</html>
```

## Diagram: Main and Cross Axis with Flex
```plaintext
.container (display: flex; flex-direction: row;)

   main axis → → →
┌────────────────────────────┐
| [Item 1]  [Item 2]  [Item 3] |  cross axis
└────────────────────────────┘
            ↑
```

## Additional Tips
1. **Mobile-First**: Combine flex with media queries for responsive designs.
2. **Use `gap`**: Instead of margins for spacing between items.
3. **Avoid Over-Nesting**: Flex containers can nest if needed, but keep it structured.
4. **Don’t Overuse `order`**: Reordering may confuse keyboard or screen-reader navigation.

## Common Pitfalls
1. **Mixed Widths**: Items with fixed widths may break flexible behavior.
2. **Overflow**: Large images or content can push flex items beyond container boundaries.
3. **IE/Legacy Support**: Older browsers (like IE10) require vendor prefixes or partial support.

## Comparison: Flexbox vs. Grid
| Aspect            | Flexbox                         | Grid                               |
|-------------------|---------------------------------|------------------------------------|
| **Layout**        | One-dimensional (row OR column) | Two-dimensional (rows AND columns) |
| **Use Cases**     | Navbars, alignment, content blocks in a line | Complex page layouts, data grids  |
| **Axis**          | main axis, cross axis           | row axis, column axis              |
| **Browser Support** | Very good (some older browsers need prefix) | Similarly good, older browsers need fallback |

## References & Recommended Resources
1. [MDN Web Docs - Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
2. [CSS-Tricks - A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
3. [W3Schools - CSS Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)

---
## ⭐️ Understanding CSS Flex-Direction
## Introduction
In Flexbox, the `flex-direction` property defines the **main axis** of a flex container, determining how flex items are laid out. Whether horizontally in a row, vertically in a column, or reversed, `flex-direction` provides foundational control over the orientation of child elements within a flex container.

## Why is `flex-direction` Important?
1. **Sets the Main Axis**: Determines whether items flow horizontally (`row`) or vertically (`column`).
2. **Key to Alignments**: The `justify-content` property aligns items along the main axis, which depends on the direction set.
3. **Responsive Design**: Switching from row to column on smaller screens can transform layouts for better usability.

### `flex-direction` Values
The `flex-direction` property accepts four values:
1. `row` (default)
2. `row-reverse`
3. `column`
4. `column-reverse`

## Visual Representation
### Axis Orientation Table
| `flex-direction` | Main Axis Direction | Cross Axis Direction |
|-------------------|---------------------|----------------------|
| `row`             | Left → Right        | Top → Bottom         |
| `row-reverse`     | Right → Left        | Top → Bottom         |
| `column`          | Top → Bottom        | Left → Right         |
| `column-reverse`  | Bottom → Top        | Left → Right         |

### Diagram
```
flex-direction: row           flex-direction: column
+-------------------+         +-------------------+
| [A] [B] [C]       |         | [A]               |
|                   |         | [B]               |
|                   |         | [C]               |
+-------------------+         +-------------------+

flex-direction: row-reverse   flex-direction: column-reverse
+-------------------+         +-------------------+
|       [C] [B] [A] |         | [C]               |
|                   |         | [B]               |
|                   |         | [A]               |
+-------------------+         +-------------------+
```

## Syntax and Values
```css
.container {
  display: flex;
  flex-direction: row; /* or row-reverse, column, column-reverse */
}
```

### `row`
- **Default** value.
- Items are placed **left to right**.
- The main axis is **horizontal**.

```css
.container {
  flex-direction: row;
}
```

**Use Case**:
- Horizontal navbars.
- Side-by-side content.

### `row-reverse`
- Items placed **right to left**.
- Main axis is still **horizontal**, but the start is on the right.

```css
.container {
  flex-direction: row-reverse;
}
```

**Use Case**:
- Reverse order for UI elements (e.g., RTL languages or design preferences).

### `column`
- Items stack **top to bottom**.
- The main axis is **vertical**.

```css
.container {
  flex-direction: column;
}
```

**Use Case**:
- Vertical stacking (like a column of cards or form fields).

### `column-reverse`
- Items stack **bottom to top**.
- Main axis is **vertical**, reversing the default order.

```css
.container {
  flex-direction: column-reverse;
}
```

**Use Case**:
- Reversing content order for certain design patterns.

## Visual Diagram
```plaintext
flex-direction: row (default)
┌─────────────────────┐
| [Item 1][Item 2][Item 3] → → →
└─────────────────────┘
        Main Axis: horizontal

flex-direction: column
┌────────┐
| Item 1 |
| Item 2 |
| Item 3 |
└────────┘
   Main Axis: vertical
```

## Combining with Other Flex Properties
### 1. `justify-content`
- Aligns items **along the main axis**.
- For `row` or `row-reverse`, it aligns horizontally.
- For `column` or `column-reverse`, it aligns vertically.

**Example**:
```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
```

### 2. `align-items`
- Aligns items **along the cross axis** (perpendicular to main axis).

**Example**:
```css
.container {
  display: flex;
  flex-direction: column;
  align-items: center; /* horizontal alignment if main axis is vertical */
}
```

### 3. `flex-wrap`
- Specifies whether flex items wrap to a new line if there’s insufficient space.

**Example**:
```css
.container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
```

## Example Code Snippet
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Flex-Direction Example</title>
<style>
  .row-container {
    display: flex;
    flex-direction: row;
    background-color: #fafafa;
    padding: 1rem;
  }

  .column-container {
    display: flex;
    flex-direction: column;
    background-color: #f0f0f0;
    padding: 1rem;
  }

  .box {
    background-color: #ccc;
    margin: 0.5rem;
    padding: 1rem;
    flex: 1;
    text-align: center;
  }
</style>
</head>
<body>
  <h1>Flex-Direction Demo</h1>

  <div class="row-container">
    <div class="box">Item 1</div>
    <div class="box">Item 2</div>
    <div class="box">Item 3</div>
  </div>

  <div class="column-container">
    <div class="box">Item A</div>
    <div class="box">Item B</div>
    <div class="box">Item C</div>
  </div>
</body>
</html>
```

In this example:
- **`.row-container`** uses the default horizontal (`row`) layout.
- **`.column-container`** stacks items vertically (`column`).

## Real-World Use Cases
1. **Navigation Menus**: Horizontal row for main nav, column layout for sidebars.
2. **Responsive Layouts**: Switching from row on wide screens to column on narrow screens.
3. **Card Grids**: Row-based or column-based item displays with `wrap`.
4. **Multi-Directional UI**: Reverse ordering for specialized designs.

## Potential Pitfalls
1. **Overriding Normal Flow**: `row-reverse` or `column-reverse` can confuse source order or accessibility.
2. **Combining Wrong Axes**: Misusing `justify-content` vs. `align-items` when you forget which is main vs. cross axis.
3. **IE/Older Browsers**: May need prefixes or polyfills for older flex implementations.

## `flex-direction` vs. CSS `direction` Property
| Property         | Purpose                          | Values                     |
|------------------|----------------------------------|----------------------------|
| `flex-direction` | Defines Flexbox layout axis      | `row`, `column`, etc.      |
| `direction`      | Sets text/writing direction      | `ltr` (default), `rtl`     |

Example of `direction`:
```css
.container {
  direction: rtl; /* Right-to-left text (e.g., Arabic) */
}
```

## References & Recommended Resources
1. [MDN Web Docs - flex-direction](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction)
2. [CSS-Tricks - A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
3. [W3Schools - Flex Direction](https://www.w3schools.com/cssref/css3_pr_flex-direction.asp)
4. [Universal selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors)
5. [Combinators](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics/Combinators)

---
## ⭐️ Understanding CSS Flex Layout
## Introduction
CSS **Flex Layout**, often referred to simply as **Flexbox**, is a layout module designed to allow more efficient, responsive, and predictable arrangements of elements. Building upon properties like `display: flex;`, `flex-direction;`, and alignment rules, Flex Layout enables both simple and complex designs with minimal code compared to older techniques like floats or tables.

## Key Concepts of Flex Layout
### 1. Flex Container
Any element with `display: flex;` (or `display: inline-flex;`) becomes a **flex container**, creating a new layout context for its **direct children** (called **flex items**).

### 2. Main Axis vs. Cross Axis
- **Main Axis**: The primary direction of the flex items (row = horizontal, column = vertical).
- **Cross Axis**: Perpendicular to the main axis, used for alignment in the opposite direction.

### Axes
- **Main Axis**: Defined by `flex-direction` (default: horizontal).
- **Cross Axis**: Perpendicular to main axis (default: vertical).

```
┌─────────────▶ Main Axis (flex-direction: row)
│
│
▼
Cross Axis
```

### 3. Flexible Sizing
Flex items can **grow** or **shrink** to fill available space, making fluid layouts straightforward.

## Container Properties
### 1. `display`
- **`flex`**: Block-level flex container.
- **`inline-flex`**: Inline-level flex container.

```css
.container {
  display: flex; /* or inline-flex */
}
```

### 2. `flex-direction`
Defines the **direction** of the main axis.

| Value          | Description                                  |
|----------------|----------------------------------------------|
| `row`          | Left to right (default)                      |
| `row-reverse`  | Right to left                                |
| `column`       | Top to bottom                                |
| `column-reverse` | Bottom to top                              |

```css
.container {
  flex-direction: row;
}
```

### 3. `flex-wrap`
Specifies whether items wrap onto a new line if there's insufficient space.

| Value          | Description                                     |
|----------------|-------------------------------------------------|
| `nowrap`       | Single line (default)                           |
| `wrap`         | Wrap items onto multiple lines                 |
| `wrap-reverse` | Wrap in reverse order                          |

```css
.container {
  flex-wrap: wrap;
}
```

### 4. `justify-content`
Aligns items along the **main axis**.

| Value            | Description                                             |
|------------------|---------------------------------------------------------|
| `flex-start`     | Items align at the start of the main axis (default)     |
| `flex-end`       | Items align at the end of the main axis                |
| `center`         | Items centered along the main axis                     |
| `space-between`  | Items have equal space between them                    |
| `space-around`   | Items have space around them (including edges)         |
| `space-evenly`   | Equal spacing between items **and** container edges    |

```css
.container {
  justify-content: center;
}
```

### 5. `align-items`
Aligns items along the **cross axis**.

| Value          | Description                                                 |
|----------------|-------------------------------------------------------------|
| `stretch`      | Items fill the container cross axis dimension (default)    |
| `flex-start`   | Items placed at cross axis start                           |
| `flex-end`     | Items placed at cross axis end                             |
| `center`       | Items centered along cross axis                            |
| `baseline`     | Items aligned according to their text baseline             |

```css
.container {
  align-items: center;
}
```

### 6. `align-content`
Controls spacing along the cross axis **when items wrap** over multiple lines.

| Value          | Description                                                   |
|----------------|---------------------------------------------------------------|
| `stretch`      | Lines expand to fill remaining space (default)               |
| `flex-start`   | Lines packed at cross axis start                             |
| `flex-end`     | Lines packed at cross axis end                               |
| `center`       | Lines centered along cross axis                              |
| `space-between`| Equal space between lines                                    |
| `space-around` | Equal space around each line                                 |
| `space-evenly` | Equal spacing between lines and container edges             |

```css
.container {
  align-content: space-between;
}
```

### 7. `gap`, `row-gap`, `column-gap`
Specifies spacing **between** flex items (similar to how grid gap works).

```css
.container {
  gap: 10px; /* or row-gap, column-gap */
}
```

## Flex Item Properties
### 1. `flex: grow shrink basis;`
Shorthand for `flex-grow`, `flex-shrink`, and `flex-basis`.

- **flex-grow**: Proportionally expands the item when extra space is available.
- **flex-shrink**: Shrinks an item if there's not enough space.
- **flex-basis**: The item's initial size before grow/shrink calculations.

```css
.item {
  flex: 1 1 100px; /* can grow or shrink, initial basis = 100px */
}
```

### 2. `order`
Changes the **visual order** of flex items (without altering the source HTML).

```css
.item1 {
  order: 2;
}
.item2 {
  order: 1;
}
```

### 3. `align-self`
Overrides `align-items` for a single item.

```css
.item {
  align-self: flex-end;
}
```

## Example: Creating a Basic Flex Layout
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Flex Layout Example</title>
  <style>
    .container {
      display: flex;
      flex-direction: row; /* Items arranged horizontally */
      justify-content: space-between; /* Space at edges, distribution in between */
      align-items: center; /* Vertically center on cross axis if row */
      gap: 10px;
      padding: 1rem;
      border: 2px solid #333;
    }

    .item {
      background-color: #f0f0f0;
      flex: 1 1 100px; /* grows/shrinks, minimum 100px */
      text-align: center;
      padding: 1rem;
    }
  </style>
</head>
<body>
  <h1>Flex Layout Demonstration</h1>
  <div class="container">
    <div class="item">Item 1</div>
    <div class="item">Item 2</div>
    <div class="item">Item 3</div>
  </div>
</body>
</html>
```

**Explanation**:
- The **container** arranges items horizontally.
- `justify-content: space-between` creates spacing between items, none at container edges.
- `align-items: center` centers them vertically.
- Each **item** can grow/shrink while maintaining a minimum width of `100px`.

## Diagram: Row-based Flex Layout
```plaintext
[ Container (flex: row) ]
 ├─ item1      ├─ item2      ├─ item3
   <---- gap=10px ---->
Justify-Content = space-between → [   item1   ][   item2   ][   item3   ]
Align-Items = center => vertically aligned
```

## Real-World Use Cases
1. **Nav Bars**: Evenly spaced links.
2. **Card Layouts**: Row or column-based distributions.
3. **Responsive Grids**: Use `flex-wrap: wrap` for multi-row layouts.
4. **Horizontal & Vertical Centering**: Achieve easy centering with a single property.
5. **Reordering**: Temporarily rearranging items for different viewport sizes.

## Potential Pitfalls
1. **Older Browser Support**: Requires prefixes or fallback for IE10 and older.
2. **Fixed vs. Fluid**: Mixed usage of `width` might override the flexibility.
3. **Excessive Nesting**: Overly nested flex containers can complicate layout.

## References & Recommended Resources
1. [MDN Web Docs - CSS Flexible Box Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout)
2. [CSS-Tricks - Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
3. [W3Schools - CSS Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)
4. [Flex Layout Testing](https://appbrewery.github.io/flex-layout/)
---
## ⭐️ Understanding CSS Flex Sizing
## Introduction
In Flexbox, sizing refers to how elements grow or shrink to fill available space within a flex container. The core mechanisms revolve around **`flex-basis`, `flex-grow`, and `flex-shrink`**, combined in the shorthand property `flex`. By mastering flex sizing, you can create adaptive layouts that behave predictably across varying screen sizes and content requirements.

## Why Flex Sizing Matters
1. **Responsive Layouts**: Items can adapt to available space without fixed widths.
2. **Eliminate Overflow**: Controlling how items shrink prevents accidental overflow.
3. **Design Consistency**: Ensures elements remain proportionate, even with dynamic content.
4. **Simplify Maintenance**: Less reliance on complicated manual calculations.

## Flex Sizing Properties
### 1. `flex-basis`
- Defines the **initial main size** of a flex item.
- Can be in `px`, `%`, `rem`, or `auto`.
- If set to `auto`, the item’s intrinsic size or content size is used.

| Value          | Behavior                          |
|----------------|-----------------------------------|
| `auto` (default)| Uses item's `width`/`height`     |
| `px`, `%`, `em`| Explicit fixed size              |
| `content`      | Sizes based on item's content    |

```css
.item {
  flex-basis: 200px; /* attempts to be 200px wide in a row layout */
}
```

### 2. `flex-grow`
- Determines **how much** a flex item **can grow** relative to other flex items **when extra space is available**.
- Default is `0` (no growth).
- A higher number means the item grows more.

```css
.item {
  flex-grow: 1; /* expands if container has extra space */
}
```

**Example**:
- If three items have `flex-grow: 1`, they each take an equal share of leftover space.
- If one item has `flex-grow: 2` and others have `flex-grow: 1`, the item with `2` gets double the leftover space.

### 3. `flex-shrink`
- Defines **how much** a flex item **shrinks** when space is limited.
- Default is `1` (items shrink as needed).
- A value of `0` prevents shrinking.

**Calculation**:
```
Negative Space = Container Size - Sum of flex-basis values
Shrink Factor = (flex-shrink × flex-basis) / Total Shrink Factors
```

```css
.item {
  flex-shrink: 0; /* item won't shrink below its flex-basis */
}
```

**Example**:
- If an item has `flex-shrink: 0`, it stays at `flex-basis` size, potentially causing overflow.
- Setting a higher shrink value compared to siblings means it shrinks more aggressively.

### 4. `flex` (Shorthand)
Combines `flex-grow`, `flex-shrink`, and `flex-basis` in a single declaration.

```css
.item {
  flex: <grow> <shrink> <basis>;
}

/* Example */
.item {
  flex: 1 1 200px; /* can grow, can shrink, starts at 200px wide */
}
```

| Shorthand   | Components                                         |
|-------------|-----------------------------------------------------|
| `1 1 auto`  | `flex-grow: 1; flex-shrink: 1; flex-basis: auto;`  |
| `0 0 auto`  | No grow, no shrink, auto basis                     |
| `1 0 100px` | Grows, no shrink, starts at 100px                   |

## How Sizing Works Together
When **extra space** exists in the container:
- Items compare their `flex-grow` values to decide how much to expand.

When **not enough space** is available:
- Items compare their `flex-shrink` values to decide how much to shrink.

**`flex-basis`** sets an initial or ideal size from which these calculations begin.

## Example: Proportional Sizing
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
  .container {
    display: flex;
    gap: 10px;
    background-color: #eee;
    padding: 10px;
  }

  .box1 {
    flex: 1 1 100px; /* grows equally, shrinks equally, starts at 100px */
    background-color: #add8e6;
    text-align: center;
    padding: 20px;
  }

  .box2 {
    flex: 2 1 100px; /* grows 2x faster than .box1 */
    background-color: #90ee90;
    text-align: center;
    padding: 20px;
  }

  .box3 {
    flex: 1 2 100px; /* normal grow, shrinks faster (2) than others (1) */
    background-color: #ffb6c1;
    text-align: center;
    padding: 20px;
  }
</style>
<title>Flex Sizing Demo</title>
</head>
<body>
  <h1>Flex Sizing Example</h1>

  <div class="container">
    <div class="box1">Box 1</div>
    <div class="box2">Box 2</div>
    <div class="box3">Box 3</div>
  </div>
</body>
</html>
```

**Explanation**:
- `.box2` has `flex-grow: 2`, so it gets double the leftover space compared to `.box1` or `.box3`.
- `.box3` has `flex-shrink: 2`, so if space is lacking, it shrinks faster than `.box1`.

## Diagram: Flex Sizing at Work
```plaintext
Container
+---------------------------------------------------------------------------+
|            Extra Space Distributed Based on flex-grow                    |
| [Box 1 flex:1] [Box 2 flex:2] [Box 3 flex:1]                             |
|   smaller  <---- leftover ---->   bigger    <---- leftover ---->  smaller |
+---------------------------------------------------------------------------+
```

## Combining with Other Flex Properties
1. **`flex-direction`**: Sizing logic applies along the main axis (horizontal if `row`, vertical if `column`).
2. **`justify-content`**: Helps distribute leftover space after items finish their own sizing.
3. **`align-items`** and `align-content`: Manages cross-axis alignment but doesn’t affect `flex-basis`.

## Common Pitfalls
1. **`flex-shrink: 0`** Overflows: If the container is too small, an item with shrink set to `0` may break the layout.
2. **Overly Large `flex-basis`**: If `flex-basis` is bigger than the container, items can overflow.
3. **Incorrect Unit Usage**: Combining `px` and `%` in ambiguous ways can cause unexpected results.


## References & Recommended Resources
1. [MDN Web Docs - Flex](https://developer.mozilla.org/en-US/docs/Web/CSS/flex)
2. [CSS-Tricks - A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
3. [W3Schools - CSS Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)
4. [Can I Use - Flexbox](https://caniuse.com/flexbox)