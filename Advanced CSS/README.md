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
## ⭐️ Creating Responsive Websites with CSS

## Introduction
**Responsive web design** (RWD) ensures that websites adapt gracefully to various devices, screen sizes, and orientations. By utilizing fluid layouts, flexible images, and media queries, developers can craft experiences that look and function optimally on desktops, tablets, and smartphones. This modern approach to CSS fosters inclusivity, accessibility, and long-term site maintainability.

## Key Characteristics of Responsive Design
1. **Fluid Grids**: Layouts that adjust proportionally based on the viewport size.
2. **Flexible Images**: Media that scales or switches source files to prevent overflow and maintain clarity.
3. **Media Queries**: Conditional rules that apply different styles at specified breakpoints.
4. **Mobile-First Approach**: Prioritizing smaller screens, then scaling up to larger devices.
5. **Performance-Driven**: Minimizing resource usage for slower networks and smaller devices.

## Foundations of Responsive CSS
### 1. The Viewport Meta Tag
For mobile devices, the following meta tag ensures proper scaling.

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
- `width=device-width` matches the device’s width.
- `initial-scale=1.0` sets the zoom level.

### 2. Fluid Layouts
Using **relative units** (`%`, `em`, `rem`, `vw`, `vh`) allows elements to adapt to changes in screen size.

```css
.container {
  width: 90%;   /* instead of fixed px width */
  margin: 0 auto;
}

h1 {
  font-size: 2em; /* scales with the base font size */
}
```

**Benefit**: Minimizes horizontal scrolling and ensures content scales for various devices.

## Media Queries
Media queries let you apply styles at **breakpoints** that suit particular screen widths or device characteristics.

### Syntax
```css
@media (max-width: 768px) {
  /* Styles for screens <= 768px wide */
}

@media (min-width: 769px) {
  /* Styles for screens >= 769px wide */
}

@media (min-width: 1024px) and (orientation: landscape) {
  /* Additional rules for wide screens in landscape mode */
}
```

### Example
```css
body {
  background-color: #fff;
}

@media (max-width: 600px) {
  body {
    background-color: #f0f0f0; /* Lighter bg for smaller screens */
  }
}
```
In this scenario, any screen **600px** wide or less gets a different background color.

## Responsive Images
### 1. Fluid Images
```css
img {
  max-width: 100%;
  height: auto;
}
```
This ensures images shrink to fit their parent container while preserving aspect ratio.

### 2. `srcset` and `sizes`
Modern HTML allows specifying multiple image files for different device pixel densities.

```html
<img 
  src="image-400.jpg" 
  srcset="image-400.jpg 400w, image-800.jpg 800w" 
  sizes="(max-width: 600px) 400px, 800px" 
  alt="A responsive example" >
```

**Benefits**:
- High-DPI devices get sharper images.
- Saves bandwidth on smaller screens.

## Mobile-First Design Strategy
1. **Default Styles**: Start with base styles for **small screens**.
2. **Progressive Enhancement**: Add complexity for larger screens using min-width breakpoints.

```css
/* Base (mobile) styles */
.container {
  display: block;
  padding: 1em;
}

/* Larger screens (tablet, desktop) */
@media (min-width: 768px) {
  .container {
    display: flex;
  }
}
```

## Tools and Frameworks
1. **Bootstrap** / **Foundation**: Prebuilt grids, responsive utilities.
2. **Tailwind CSS**: Utility-first approach with responsive classes.
3. **CSS Grid** / **Flexbox**: Native layout modules for advanced responsiveness.
4. **Media Query Mixins** (SASS/LESS): Simplify repetitive breakpoints.

## Example Code: Simple Responsive Layout
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Web Example</title>
  <style>
    body {
      margin: 0;
      font-family: sans-serif;
    }

    header, footer {
      background-color: #333;
      color: #fff;
      padding: 1rem;
      text-align: center;
    }

    .container {
      display: flex;
      flex-wrap: wrap;
      margin: 0 auto;
      max-width: 1200px;
      padding: 1rem;
    }

    .box {
      flex: 1 1 300px;
      background-color: #f0f0f0;
      margin: 0.5rem;
      padding: 1rem;
    }

    /* Media Query for smaller screens */
    @media (max-width: 600px) {
      .box {
        flex: 1 1 100%;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Responsive Example</h1>
  </header>

  <div class="container">
    <div class="box">Box 1</div>
    <div class="box">Box 2</div>
    <div class="box">Box 3</div>
    <div class="box">Box 4</div>
  </div>

  <footer>
    <p>&copy; 2025 Responsive Design</p>
  </footer>
</body>
</html>
```

## Key Techniques & Tools
### 1. CSS Grid
- **Use Case**: Two-dimensional layouts (rows and columns).
  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
  }
  ```

### 2. Flexbox
- **Use Case**: One-dimensional layouts (rows or columns).
  ```css
  .nav {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap; /* Wraps items on smaller screens */
  }
  ```

### 3. Relative Units
| **Unit** | **Description**                  | **Example**               |
|----------|-----------------------------------|---------------------------|
| `%`      | Relative to parent container     | `width: 50%;`             |
| `vw/vh`  | Relative to viewport dimensions  | `width: 100vw;`           |
| `rem`    | Relative to root font size       | `font-size: 1.5rem;`      |

### 4. Breakpoints (Common Media Query Ranges)
| **Device Type** | **Breakpoint** | **Use Case**               |
|-----------------|-----------------|----------------------------|
| Mobile          | < 768px         | Portrait phones            |
| Tablet          | 768px – 1024px  | Landscape phones, tablets  |
| Desktop         | > 1024px        | Desktops, laptops          |

## Step-by-Step Implementation
### 1. Mobile-First Approach
- **Strategy**: Design for mobile screens first, then enhance for larger devices.
- **Example**:
  ```css
  /* Base styles (mobile) */
  .card { padding: 10px; }

  /* Tablet styles */
  @media (min-width: 768px) {
    .card { padding: 20px; }
  }

  /* Desktop styles */
  @media (min-width: 1024px) {
    .card { padding: 30px; }
  }
  ```

### 2. Responsive Navigation
- **Hamburger Menu**:
  ```html
  <nav class="nav">
    <button class="menu-toggle">☰</button>
    <ul class="nav-links">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
    </ul>
  </nav>
  ```
  ```css
  .nav-links {
    display: none;
  }
  @media (min-width: 768px) {
    .menu-toggle { display: none; }
    .nav-links { display: flex; }
  }
  ```

### 3. Responsive Images
- **Art Direction** with `<picture>`:
  ```html
  <picture>
    <source media="(min-width: 768px)" srcset="large.jpg">
    <source media="(min-width: 480px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive image">
  </picture>
  ```

## Testing & Debugging
- **Tools**:
  - **Chrome DevTools**: Device toolbar for simulating screens.
  - **BrowserStack**: Cross-device testing.
- **Best Practice**: Test on real devices for touch/performance issues.

## Common Pitfalls & Solutions
| **Issue**                | **Solution**                                 |
|--------------------------|----------------------------------------------|
| Overflowing content      | Use `overflow: hidden` or `scroll`           |
| Unresponsive images      | Apply `max-width: 100%` and `height: auto`   |
| Breakpoint conflicts     | Organize media queries from small to large   |

## Frameworks & Libraries
| **Tool**       | **Purpose**                       |
|----------------|-----------------------------------|
| Bootstrap      | Pre-built responsive components   |
| Tailwind CSS   | Utility-first responsive classes  |
| Foundation     | Customizable grid system          |

In this example:
- **Flexbox** manages columns.
- **Media Query** adjusts layout when **max-width** is **600px** or below.

## Potential Pitfalls
1. **Overlapping Breakpoints**: Ensure your media queries don’t conflict.
2. **Excessive CSS**: Keep breakpoints strategic, not every 10px.
3. **Testing**: Check multiple devices or use simulators to confirm usability.
4. **Performance**: Large images can hurt load times if not optimized properly.

## References & Recommended Resources
1. [MDN Web Docs - Responsive Design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)
2. [W3Schools - RWD Tutorial](https://www.w3schools.com/css/css_rwd_intro.asp)
3. [CSS-Tricks - Responsive Web Design Basics](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
4. [Google Web Fundamentals](https://developers.google.com/web/fundamentals/design-and-ux/responsive)
5. [Can I Use - Browser Support](https://caniuse.com/)

---
## ⭐️ Understanding CSS Media Queries

## Introduction
**CSS Media Queries** are a foundational tool in responsive web design. They allow developers to apply different styles based on a device’s characteristics, such as screen width, height, resolution, or orientation. By using media queries, a website can adapt its layout and design for various devices—desktops, tablets, phones—ensuring better usability and aesthetics.

## What Are Media Queries?
Media queries are conditional rules in CSS that test a device’s features. When the conditions are met, the styles within the query take effect. In other words, they apply specific CSS only if certain **media features** match.

### Syntax Overview
```css
@media (feature: value) {
  /* CSS rules here apply only if the feature matches the given value */
}
```

For example, `@media (max-width: 600px)` targets screens with a width **up to** 600px.

## Key Characteristics
1. **Conditional Styling**: Applies different CSS rules depending on device features.
2. **Multiple Conditions**: Combine features using logical operators (`and`, `not`, `or` via commas).
3. **Mobile-First**: Often used starting with base (mobile) styles, then additional queries for larger screens.
4. **Wide Range of Features**: `width`, `height`, `orientation`, `aspect-ratio`, `resolution`, etc.

### Media Features
| Feature          | Description                  | Example                     |
|------------------|------------------------------|-----------------------------|
| `width`          | Viewport width               | `(min-width: 768px)`        |
| `orientation`    | Portrait/landscape mode      | `(orientation: landscape)`  |
| `resolution`     | Device pixel density         | `(min-resolution: 2dppx)`   |
| `hover`          | Hover capability             | `(hover: hover)`            |
| `prefers-color-scheme` | Dark/light mode preference | `(prefers-color-scheme: dark)` |

### Logical Operators
| Operator   | Description                     | Example                                   |
|------------|---------------------------------|-------------------------------------------|
| `and`      | Combines conditions             | `@media (min-width: 600px) and (max-width: 1200px)` |
| `,`        | Logical OR                      | `@media (max-width: 600px), (print)`      |
| `not`      | Negates the query               | `@media not screen and (color)`           |
| `only`     | Targets modern browsers         | `@media only screen and (min-width: 768px)` |

## Basic Examples
### Example 1: `max-width` Breakpoint
```css
/* Styles for screens up to 600px wide */
@media (max-width: 600px) {
  body {
    background-color: #fafafa;
  }
  .container {
    padding: 10px;
  }
}
```

### Example 2: `min-width` Breakpoint
```css
/* Styles for screens 768px or wider */
@media (min-width: 768px) {
  .sidebar {
    float: left;
    width: 25%;
  }
  .main-content {
    width: 75%;
    float: left;
  }
}
```

### Example 3: Combining Features
```css
@media (min-width: 768px) and (orientation: landscape) {
  .landscape-layout {
    display: flex;
  }
}
```
Applies styles only if the viewport is **at least 768px wide** and the device is in **landscape** orientation.

## Logical Operators
1. **and**: Both conditions must be true.
2. **not**: Negates a media query.
3. **,** (comma): Functions like **OR**—separates multiple media queries.

**Example**:
```css
@media (min-width: 768px) and (max-width: 1024px) {
  /* styles for tablets between 768px and 1024px wide */
}

@media screen and (max-width: 600px), screen and (max-height: 600px) {
  /* if either width <= 600px OR height <= 600px */
}
```

## Media Types vs. Media Features
| Media Type | Description                                          |
|------------|------------------------------------------------------|
| `screen`   | Typical displays (desktop, tablet, phone)           |
| `print`    | For printed materials or print preview              |
| `speech`   | Screenreaders reading out loud                      |

**Media Features** focus on device specifics such as **width**, **height**, **orientation**, **resolution**, etc.

## Diagram: Media Query Flow
```plaintext
                     +----------+
    Device Width --->| Condition|---> If true, apply media query rules
    Orientation   --->|   Check  |
                     +----------+

```

## Common Breakpoint Patterns
| Breakpoint     | Typical Use Case                            |
|----------------|---------------------------------------------|
| 0–600px        | Small phones                                |
| 600–768px      | Larger phones, smaller tablets              |
| 768–1024px     | Tablets, small laptops                      |
| 1024px+        | Desktops, large screens                     |

**Note**: There’s no universal standard for breakpoints. Tailor them to your design.

## Example: Mobile-First Approach
```css
/* Base mobile styles */
body {
  font-size: 16px;
  margin: 0;
}

/* Tablet screens and up */
@media (min-width: 768px) {
  body {
    font-size: 18px;
  }
}

/* Desktop screens and up */
@media (min-width: 1024px) {
  body {
    font-size: 20px;
  }
}
```

## Potential Pitfalls
1. **Too Many Breakpoints**: Creates complex code that’s hard to maintain.
2. **Ignoring Device Capabilities**: Overly focusing on width instead of orientation, resolution, etc.
3. **Browser Incompatibilities**: Older browsers have partial support for certain features (check [caniuse.com](https://caniuse.com/)).

## Example of Combining Media Queries for a Responsive Layout
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Media Queries Demo</title>
<style>
  body {
    margin: 0;
    font-family: Arial, sans-serif;
  }

  header {
    background-color: #333;
    color: white;
    padding: 1rem;
    text-align: center;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    margin: 0 auto;
  }

  .sidebar {
    flex: 0 0 100%;
    background-color: #f4f4f4;
    padding: 1rem;
  }

  .main {
    flex: 0 0 100%;
    padding: 1rem;
  }

  /* Tablet up */
  @media (min-width: 768px) {
    .sidebar {
      flex: 0 0 30%;
    }
    .main {
      flex: 0 0 70%;
    }
  }

  /* Desktop up */
  @media (min-width: 1024px) {
    .sidebar {
      flex: 0 0 25%;
    }
    .main {
      flex: 0 0 75%;
    }
  }
</style>
</head>
<body>
  <header>
    <h1>Responsive Demo with Media Queries</h1>
  </header>

  <div class="container">
    <div class="sidebar">
      <h2>Sidebar</h2>
      <p>This section changes width based on breakpoints.</p>
    </div>
    <div class="main">
      <h2>Main Content</h2>
      <p>Lorem ipsum dolor sit amet...</p>
    </div>
  </div>
</body>
</html>
```

## References & Recommended Resources
1. [MDN Web Docs - Using Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
2. [CSS-Tricks - Media Queries](https://css-tricks.com/css-media-queries/)
3. [W3Schools - CSS Media Queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp)
4. [caniuse.com - Browser Support](https://caniuse.com/)

---
## ⭐️ 

---
## ⭐️ 