# Intermediate CSS

---
## ⭐️ Understanding CSS Specificity and Inheritance

## Introduction
CSS specificity and inheritance are fundamental concepts that dictate how the browser determines which styles apply to an element. Specificity refers to the "weight" or "priority" of CSS selectors, while inheritance describes how certain properties pass from parent elements to their children. Mastering these concepts helps you troubleshoot conflicting styles and build maintainable, predictable style sheets.

## Part 1: CSS Specificity

### What is Specificity?
**Specificity** is the mechanism by which the browser decides which CSS declaration takes precedence when multiple declarations target the same element.

### How Specificity Works
Each selector in CSS has a "weight" based on:
1. **Inline styles** (e.g., `style="color: red;"`) – highest.
2. **ID selectors** (e.g., `#header`)
3. **Class selectors** (e.g., `.container`), **attribute selectors** (e.g., `a[href]`), and **pseudo-classes** (e.g., `:hover`)
4. **Element selectors** (e.g., `div`, `p`), and **pseudo-elements** (e.g., `::before`)

When two or more rules conflict, the one with the higher specificity wins.

### Specificity Scoring
A typical way to count specificity is using a triplet or quadruplet notation (e.g., `(A, B, C)` or `(A, B, C, D)`):
- **A**: Number of inline styles.
- **B**: Number of ID selectors.
- **C**: Number of class, attribute, and pseudo-class selectors.
- **D**: Number of element and pseudo-element selectors.

| Selector Type          | Example          | Specificity Value |
|------------------------|------------------|-------------------|
| Inline style           | `style="..."`    | `(1, 0, 0, 0)`    |
| ID selector            | `#header`        | `(0, 1, 0, 0)`    |
| Class selector         | `.button`        | `(0, 0, 1, 0)`    |
| Element selector       | `div`            | `(0, 0, 0, 1)`    |

### Rules of Specificity
1. **Higher specificity** wins over lower specificity.
2. **Inline styles** override external/internal stylesheets.
3. The `!important` keyword trumps all specificity (use sparingly).

For example:
```css
/* Example 1: h1 has (0,0,0,1) specificity */
h1 {
    color: blue;
}

/* Example 2: .title has (0,0,1,0) specificity */
.title {
    color: green;
}

/* Example 3: #main has (0,1,0,0) specificity */
#main {
    color: red;
}
```
A higher value in the first part of the notation is always more specific than any values in the latter parts.

### !important Keyword
- **Forces** a declaration to override other declarations, even those with higher specificity.
- Generally discouraged in production code unless absolutely necessary (e.g., utility classes, third-party overrides).

```css
.box {
  color: black !important;
}
```

**Drawbacks**:
- Harder to maintain, can break the cascading logic.

## Part 2: CSS Inheritance

### What is Inheritance?
**Inheritance** is the concept where certain CSS properties applied to a parent element are **inherited** by its child elements. For instance, setting `font-family` on a `<body>` element often applies to all nested text.

### Inheritable vs. Non-Inheritable Properties
- **Inheritable**: `color`, `font-family`, `font-size`, `line-height`, etc.
- **Non-Inheritable**: `margin`, `border`, `padding`, `width`, `height`, etc.

### Controlling Inheritance
- **Inherit**: Force a child to inherit a parent’s value.
- **Initial**: Reset to the browser’s default value.
- **Unset**: Acts as `inherit` or `initial` based on the property’s default behavior.

### The `inherit` Keyword
- Forces a property to explicitly adopt the same value as its parent.

```css
.child {
    color: inherit; /* inherits parent color even if child has a separate rule elsewhere */
}
```

### The `initial` Keyword
- Resets a property to its default initial value.

```css
.child {
    color: initial; /* reverts color property to the browser’s default */
}
```

### The `unset` Keyword
- Resets a property to "inherit" if it is naturally inheritable, or "initial" if it is not.

```css
.child {
    color: unset;
}
```

## Combining Specificity and Inheritance
1. **Inheritance** applies automatically, but can be overridden by more specific selectors.
2. **Specificity** decides which rule wins if multiple rules set the same property.
3. **!important** can override both, but use sparingly.

## Examples

### Example 1: Conflicting Rules
```html
<!DOCTYPE html>
<html>
<head>
<style>
  body {
    color: blue; /* inherited by child elements unless overridden */
  }
  p {
    color: green;
  }
  .special {
    color: red;
  }
</style>
</head>
<body>
  <div>
    <p>This paragraph is <span class="special">partially special</span>.</p>
  </div>
</body>
</html>
```
1. `body { color: blue; }` sets the default color to blue.
2. `p { color: green; }` overrides the body color for `<p>` elements.
3. `.special { color: red; }` overrides the `<p>` color specifically for elements with the class `special`.

### Example 2: Inline Styles vs. External Styles
```html
<!DOCTYPE html>
<html>
<head>
<style>
  .highlight {
    background-color: yellow;
  }
</style>
</head>
<body>
  <p class="highlight" style="background-color: lime;">
    This background is lime because inline styles have higher specificity.
  </p>
</body>
</html>
```
1. The inline style `style="background-color: lime;"` overrides `.highlight { background-color: yellow; }`.

### Example 3: Inheritance
```html
<!DOCTYPE html>
<html>
<head>
<style>
  body {
    font-size: 16px; /* inherited by h1 and p by default */
  }
  .container {
    color: darkslategray; /* child elements will inherit this color */
  }
</style>
</head>
<body>
  <div class="container">
    <h1>This inherits color: darkslategray</h1>
    <p>And this text also inherits the same color.</p>
  </div>
</body>
</html>
```

## Diagram: Specificity Hierarchy
```plaintext
            Inline Styles (style="...") [Highest]
                  /\
                  ||
   ID Selectors (#id)
                  /\
                  ||
   Class, Attribute, Pseudo-class (.class, [attr], :hover)
                  /\
                  ||
   Element, Pseudo-element (p, ::before) [Lowest]
```
## Specificity Calculation Flowchart
```
Inline Styles → IDs → Classes/Attributes → Elements → Browser Defaults
```
### Inherited vs Non-Inherited Properties
| Inherited Properties      | Non-Inherited Properties |
|---------------------------|--------------------------|
| `color`                   | `margin`                 |
| `font-family`             | `padding`                |
| `line-height`             | `border`                 |
| `text-align`              | `background`             |

## References & Recommended Resources
1. [MDN Web Docs - Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)
2. [MDN Web Docs - Inheritance](https://developer.mozilla.org/en-US/docs/Web/CSS/inheritance)
3. [CSS-Tricks - Specifics on CSS Specificity](https://css-tricks.com/specifics-on-css-specificity/)

---
## ⭐️ Combining CSS Selectors in Web Development

## Introduction
In CSS, selectors define which elements should receive a set of style rules. While single selectors (like `.class` or `#id`) can be powerful, **combining selectors** unlocks more complex targeting. By mixing **descendants, children, siblings, and attribute** selectors, you can apply styling precisely without scattering extraneous classes or resorting to overly specific IDs.

## Why Combine Selectors?
1. **Fine-Grained Control**: Target elements within specific contexts.
2. **Avoid Overusing Classes**: Rely on the document structure to style elements.
3. **Improve Maintainability**: Organized rules with fewer class declarations.
4. **Prevent Conflicts**: Ensures certain styles only apply in particular nesting or sibling scenarios.

## Common Combinators
### 1. Descendant Combinator (` `)
- Represented by a **space** between selectors.
- Selects elements that are **descendants** (at any depth) of another element.

```css
section p {
  color: blue;
}
```
Here, **all `<p>` elements** inside a `<section>` will be blue, regardless of nesting depth.

### 2. Child Combinator (`>`)
- Selects **direct children** of an element.

```css
ul > li {
  list-style-type: none;
}
```
Only **immediate `<li>` children** of a `<ul>` are styled, ignoring nested lists.

### 3. Adjacent Sibling Combinator (`+`)
- Targets an element that **immediately follows** a sibling.

```css
h2 + p {
  margin-top: 0;
}
```
Every `<p>` that appears **right after** an `<h2>` will have no top margin.

### 4. General Sibling Combinator (`~`)
- Selects elements that share a parent and appear **after** a specified sibling (not necessarily immediately).

```css
h2 ~ p {
  color: gray;
}
```
All `<p>` elements **after** an `<h2>` in the same parent are styled.

## Combining Class, ID, and Type Selectors
1. **Class + Type Selector**
   ```css
   p.highlight {
     background-color: yellow;
   }
   ```
   This targets `<p>` elements **with the `highlight` class** only.

2. **ID + Class**
   ```css
   #container .box {
     border: 2px solid #ccc;
   }
   ```
   Finds elements **with class `box`** that exist inside an element **with the ID `container`**.

3. **Multiple Classes**
   ```css
   .card.info {
     color: blue;
   }
   ```
   Targets elements that have **both `card` and `info` classes** (e.g., `<div class="card info">`).

## Attribute Selectors in Combination

### Examples
```css
/* Links that start with "https" within the .external class */
.external a[href^="https"] {
  color: red;
}

/* Inputs inside a form with type="email" */
form input[type="email"] {
  border: 1px solid green;
}
```
By combining **class selectors** with **attribute selectors**, you can style elements only in certain contexts.

## Pseudo-Class Combinations

1. **Hover + Descendant**
   ```css
   nav ul li:hover a {
     text-decoration: underline;
   }
   ```
   When a user hovers over an `<li>` in a navigation, its `<a>` child is underlined.

2. **Focus Within a Form**
   ```css
   form input:focus {
     outline: 2px solid #007bff;
   }
   ```

3. **Pseudo-Class + Sibling**
   ```css
   .tab.active + .tab {
     border-left: none;
   }
   ```
   If an element with `.tab.active` is followed by another `.tab`, remove the left border.

## Diagram: Combining Selectors
```plaintext
body > main.content div.box.highlight + p.info {
  color: #333;
}

Hierarchy of specificity:
 body > main.content -> direct child main with class="content"
 main.content div.box.highlight -> a descendant <div> with classes .box and .highlight
 box.highlight + p.info -> the <p> with class .info that immediately follows .box.highlight
```

## Performance Considerations
- Overly complex selectors (deep descendant combinators, multiple nesting) can slow rendering slightly.
- However, modern browsers are optimized, so focus on **maintainability** over micro-optimizations.

## Comparison Table: Combinators
| Combinator  | Symbol | Match Type                         | Example     |
|-------------|--------|------------------------------------|-------------|
| Descendant  | (space)| Any depth inside parent            | `div p`     |
| Child       | `>`    | Direct child of parent             | `ul > li`   |
| Adjacent    | `+`    | Immediately following sibling      | `h2 + p`    |
| General     | `~`    | Any sibling after target in parent | `h2 ~ p`    |

## Specificity Hierarchy Table
| Selector Type          | Example          | Specificity Score (A-B-C-D) |
|------------------------|------------------|-----------------------------|
| Inline Style           | `style="..."`    | 1-0-0-0                     |
| ID                     | `#header`        | 0-1-0-0                     |
| Class/Attribute/Pseudo | `.active`        | 0-0-1-0                     |
| Element/Pseudo-element | `div`            | 0-0-0-1                     |

## References & Recommended Resources
1. [MDN Web Docs - CSS Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)
2. [CSS-Tricks - Selectors](https://css-tricks.com/almanac/selectors/)
3. [W3Schools - CSS Combinators](https://www.w3schools.com/css/css_combinators.asp)
4. [HTML Living Standard](https://html.spec.whatwg.org/)

---
## ⭐️ Understanding CSS Positioning

## Introduction
In CSS, the `position` property controls how elements are laid out and how they interact with each other in the normal document flow. Different positioning schemes—such as **static**, **relative**, **absolute**, **fixed**, and **sticky**—allow you to create complex layouts, floating elements, or pinned headers.

## Types of CSS Positioning <a name="types-of-css-positioning"></a>
The `position` property accepts five values:
1. **Static** (default)
2. **Relative**
3. **Absolute**
4. **Fixed**
5. **Sticky**

### Comparison Table
| Position Value | Behavior                                                                 | Offset Properties (top/right/bottom/left) | Relative To                  |
|----------------|--------------------------------------------------------------------------|-------------------------------------------|------------------------------|
| `static`       | Element flows in normal document flow.                                   | **Ignored**                               | N/A                          |
| `relative`     | Adjusted from normal position without affecting others.                 | **Applied**                               | Its original position        |
| `absolute`     | Removed from flow; positioned relative to nearest positioned ancestor.  | **Applied**                               | Closest `relative`/`absolute`/`fixed` parent |
| `fixed`        | Removed from flow; positioned relative to viewport.                     | **Applied**                               | Viewport (screen)            |
| `sticky`       | Toggles between `relative` and `fixed` based on scroll position.        | **Applied**                               | Nearest scrollable ancestor  |

## Overview of Position Values
| Value      | Description                                                           | Typical Use Case                                         |
|------------|-----------------------------------------------------------------------|----------------------------------------------------------|
| `static`   | Default positioning; elements appear in normal flow without offset   | General page content                                     |
| `relative` | Positioned relative to its original position without removing it from normal flow | Small positional tweaks or creating a reference for absolutely positioned children    |
| `absolute` | Removed from normal flow, positioned relative to the nearest positioned ancestor | Pop-ups, overlays, or elements that need precise placement  |
| `fixed`    | Removed from normal flow, positioned relative to the **viewport**    | Sticky headers, floating menus, back-to-top buttons       |
| `sticky`   | Scroll-based hybrid of relative and fixed (newer feature)            | Sticky table headers, pinned sections while scrolling     |

## Static Positioning
- **Default** for all elements when no other positioning is set.
- Element remains in the normal document flow.
- Top/left/right/bottom properties **do not apply**.

```css
.box {
  position: static; /* or omit this property entirely */
}
```

**Key Point**: Static elements can’t be moved with top/left offsets.

## Relative Positioning
- The element is **still in the normal flow**, but you can shift it by top/left/right/bottom.
- Offsets do **not** affect other elements’ positions.
- Creates a **positioning context** for absolute children.

```css
.box {
  position: relative;
  top: 20px;     /* Moves the box 20px down from original position */
  left: 10px;    /* Moves the box 10px to the right */
}
```

**Key Uses**:
1. Slight **adjustments** to an element’s position.
2. **Containing Block** for absolutely positioned child elements.

## Absolute Positioning
- **Removed** from the normal flow; does not affect or get affected by nearby elements’ default positions.
- Positioned **relative to the nearest positioned ancestor** (`position: relative`, `absolute`, `fixed`, or `sticky`). If none is found, it uses the **viewport**.
- `top`, `left`, `right`, and `bottom` determine the final position.

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 0;
  left: 0;
  width: 100px;
  height: 100px;
}
```

**Key Uses**:
1. **Overlay** or **layer** elements (like modals or tooltips).
2. Place items **precisely** within a container.

**Diagram**:
```plaintext
.parent (relative)
 └─ .child (absolute)   // child is positioned at top-left of parent
```

## Fixed Positioning
- **Removed** from normal flow.
- Positioned **relative to the browser window (viewport)**, even as you scroll.
- `top`, `right`, `left`, `bottom` define exact location.

```css
.fixed-banner {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: #333;
}
```

**Key Uses**:
1. **Sticky navbars** or **headers**.
2. **Back-to-top** buttons that always appear.

## Sticky Positioning
- Relatively new feature: toggles between **relative** and **fixed** based on scroll position.
- An element with `position: sticky` **acts** like `relative` until a specified offset is met; then it “sticks” like **fixed**.
- Requires `top`, `left`, `right`, or `bottom` offset to work.

```css
.sticky-header {
  position: sticky;
  top: 0; /* sticks to the top after scrolling beyond the element’s position */
  background-color: #eee;
}
```

**Key Uses**:
1. **Table headers** that remain visible.
2. Section headings that remain pinned.

**Diagram**:
```plaintext
| sticky-header (position: sticky; top:0) |
|-----------------------------------------|
 scroll down...
 once the header reaches the top, it remains pinned
```

## Z-Index and Positioning
- **z-index** only applies to **positioned** elements.
- Controls stacking order.

```css
.overlay {
  position: absolute;
  z-index: 9999;
}
```

## Comparing Position Schemes
| Position | Removed from Flow? | Reference Context                       | Typical Use                        |
|----------|--------------------|-----------------------------------------|------------------------------------|
| static   | No                 | Normal document flow                    | Default for most elements          |
| relative | No                 | Element’s own original position         | Small offsets, create a container  |
| absolute | Yes                | Nearest positioned ancestor or viewport | Tooltips, overlays, advanced layouts|
| fixed    | Yes                | Viewport (browser window)               | Sticky navbars, persistent banners |
| sticky   | No -> Yes          | Scroll position (toggle)                | Sticky headers, pinned columns     |

## Examples
### Example 1: Relative and Absolute Combo
```html
<div class="relative-container">
  <div class="absolute-child">I’m absolutely positioned!</div>
</div>

<style>
.relative-container {
  position: relative;
  width: 300px;
  height: 200px;
  background-color: #f0f0f0;
}
.absolute-child {
  position: absolute;
  top: 50px;
  left: 50px;
  background-color: tomato;
}
</style>
```

### Example 2: Fixed Navbar
```html
<nav class="fixed-nav">Home | About | Contact</nav>

<style>
.fixed-nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #333;
  color: #fff;
  padding: 10px;
}
body {
  margin-top: 50px; /* to ensure content isn’t hidden under the fixed nav */
}
</style>
```

### Example 3: Sticky Header
```html
<header class="sticky-header">I stick at the top when you scroll!</header>
<main>
  <!-- long content -->
</main>

<style>
.sticky-header {
  position: sticky;
  top: 0;
  background-color: lightblue;
  padding: 15px;
}
</style>
```

## References & Recommended Resources
1. [MDN Web Docs - CSS position](https://developer.mozilla.org/en-US/docs/Web/CSS/position)
2. [CSS-Tricks - Absolute, Relative, Fixed Positioning](https://css-tricks.com/absolute-relative-fixed-positioining-how-do-they-differ/)
3. [W3Schools - CSS Layout - The position Property](https://www.w3schools.com/css/css_positioning.asp)
4. [Can I Use - Sticky Positioning](https://caniuse.com/css-sticky)