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
## ⭐️ Understanding HTML Anchor Elements (`<a>`)

## Introduction
The HTML anchor element (`<a>`) is used to create hyperlinks, which are clickable links that navigate users to different sections within the same page, other pages on the same website, or pages on entirely different websites. It is one of the core elements that makes the World Wide Web a linked network of information.

## What is an Anchor Element?
An **anchor element** in HTML is represented by the `<a>` tag. When combined with various attributes, it provides the functionality to connect webpages internally or externally.

### Key Characteristics:
1. **Hyperlink Reference**: The `href` attribute typically specifies the destination of the link, which can be an internal ID, another webpage, or an external site.
2. **Clickable Text or Media**: By default, the content inside `<a>` is displayed as clickable text, but you can also embed images or other elements.
3. **Inline Element**: Anchors are inline by nature, meaning they don't create new lines unless styled with CSS.
4. **Navigation**: They are integral to creating a navigable experience, linking to various sections or resources.

## Basic Syntax
```html
<a href="URL" target="_blank" rel="noopener noreferrer">Link Text</a>
```

### Common Attributes
- **`href`**: Specifies the link's destination.
- **`target`**: Determines where the linked document opens.
  - `_self` (default): Opens in the same tab.
  - `_blank`: Opens in a new tab.
- **`rel`**: Provides a relationship between the current document and the linked one. Common values:
  - `noopener` / `noreferrer` (for security reasons when `target="_blank"`).
- **`title`**: Adds additional information (often displayed as a tooltip on hover).
- **`download`**: Makes the link downloadable if it leads to a file.

### Example
```html
<p>
    For more information, visit <a href="https://www.example.com">Example Website</a>.
</p>
```

## Internal vs. External Links
1. **Internal Links**: Direct users to different sections or pages within the same website.
   ```html
   <a href="/about">About Us</a>
   ```
2. **External Links**: Link to pages on other websites.
   ```html
   <a href="https://www.google.com" target="_blank" rel="noopener noreferrer">Go to Google</a>
   ```

## Using Anchor Elements for Page Sections
Anchors can also navigate to specific sections on a page using IDs.

### Example of Same-Page Navigation
```html
<!-- Table of Contents -->
<ul>
    <li><a href="#section1">Section 1</a></li>
    <li><a href="#section2">Section 2</a></li>
</ul>

<!-- Content -->
<h2 id="section1">Section 1</h2>
<p>Content for section 1...</p>

<h2 id="section2">Section 2</h2>
<p>Content for section 2...</p>
```
- **Note**: The `href="#section1"` links to the element with `id="section1"`.

## Advanced Usage
1. **Embedding Images**:
   ```html
   <a href="https://www.example.com">
       <img src="example.jpg" alt="Example Image">
   </a>
   ```
2. **Email Links**:
   ```html
   <a href="mailto:example@example.com">Send Email</a>
   ```
3. **Tel Links** (for phone calls on mobile):
   ```html
   <a href="tel:+1234567890">Call Us</a>
   ```
4. **Styling**:
   ```css
   a {
       text-decoration: none;
       color: blue;
   }
   a:hover {
       text-decoration: underline;
   }
   ```

## Comparison Table
| Attribute         | Description                                               | Example Value                |
|-------------------|-----------------------------------------------------------|------------------------------|
| `href`            | URL or path to the linked page or resource               | `"https://example.com"`     |
| `target`          | Where to open the linked document                        | `_blank`, `_self`, `_parent` |
| `rel`             | Relationship between the current page and the linked doc | `noopener`, `noreferrer`     |
| `title`           | Additional tooltip information                           | `"Click for more details"`   |
| `download`        | Indicates link should be downloaded rather than visited  | `"filename.pdf"`            |

## Visual Diagram
Below is a simple representation illustrating anchor elements:

```plaintext
<a href="https://example.com">
    Link Text or <img src="image.jpg" alt="Image"> (Clickable)
</a>
```

1. `href` points to a URL or resource.
2. Content inside `<a>` is clickable.
3. You can style or modify the link appearance with CSS.

## References & Recommended Resources
1. [MDN Web Docs - `<a>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)
2. [W3Schools - HTML Links](https://www.w3schools.com/html/html_links.asp)
3. [HTML Living Standard](https://html.spec.whatwg.org/)

---
## ⭐️ Understanding HTML Global Attributes

## Introduction
In HTML, **global attributes** are attributes that can be applied to any HTML element, regardless of the element’s specific function or type. They help enhance the functionality, accessibility, and behavior of elements across a webpage.

## What Are Global Attributes?
Global attributes are common attributes recognized by all HTML elements. This means you can add them to a `<div>`, `<p>`, `<span>`, or any other valid element. Understanding how these attributes work and when to use them is essential for creating semantic, accessible, and interactive content.

### Key Characteristics:
1. **Universally Supported**: Every HTML element can include global attributes.
2. **Optional**: They are not mandatory but can add significant value when used properly.
3. **Browser Compatibility**: These attributes are standardized, so they typically work across all major browsers.

## Common HTML Global Attributes
Below is a list of frequently used global attributes:

1. **`class`**
   - **Description**: Specifies one or more class names for an element, primarily used for CSS or JavaScript.
   - **Example**:
     ```html
     <p class="highlight">This paragraph is highlighted by a CSS class.</p>
     ```

2. **`id`**
   - **Description**: Defines a unique identifier for the element, crucial for anchoring, scripting, and styling.
   - **Example**:
     ```html
     <div id="main-content">This is the main content area.</div>
     ```

3. **`style`**
   - **Description**: Embeds inline CSS styles directly onto an element.
   - **Example**:
     ```html
     <span style="color: red; font-weight: bold;">Important!</span>
     ```
   - **Note**: Using external or internal CSS is typically recommended for better maintainability.

4. **`title`**
   - **Description**: Provides advisory text, often displayed as a tooltip.
   - **Example**:
     ```html
     <button title="Click here to submit">Submit</button>
     ```

5. **`data-*`**
   - **Description**: Allows embedding custom data attributes into elements for use in scripts or styling.
   - **Example**:
     ```html
     <div data-user-id="12345">User Details</div>
     ```

6. **`hidden`**
   - **Description**: Hides the element from view, although it remains in the DOM.
   - **Example**:
     ```html
     <p hidden>This paragraph is not visible.</p>
     ```

7. **`tabindex`**
   - **Description**: Specifies whether elements can receive focus via keyboard navigation.
   - **Example**:
     ```html
     <input type="text" tabindex="1" placeholder="First field">
     <input type="text" tabindex="2" placeholder="Second field">
     ```

8. **`draggable`**
   - **Description**: Enables drag-and-drop behavior.
   - **Values**: `true`, `false`, `auto`.
   - **Example**:
     ```html
     <img src="image.jpg" draggable="true" alt="Draggable Image">
     ```

9. **`spellcheck`**
   - **Description**: Specifies whether the element is checked for spelling errors.
   - **Values**: `true`, `false`.
   - **Example**:
     ```html
     <textarea spellcheck="false">Spell check disabled here.</textarea>
     ```

## Diagram: Global Attributes Within an Element

```plaintext
<element id="uniqueId" class="classNames" style="..." title="Tooltip" data-custom="value" hidden>
    Element Content
</element>
```

1. **`id`**: Unique identifier.
2. **`class`**: Categorizes the element for styling or scripting.
3. **`style`**: Inline styling.
4. **`title`**: Hover text.
5. **`data-*`**: Custom data attribute.
6. **`hidden`**: Hides element from view.

## Example: Combining Multiple Global Attributes
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Global Attributes Example</title>
    <style>
        .highlight {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <div id="container" class="highlight" style="padding: 10px;" data-role="info-panel">
        <h1 title="This is a heading">Global Attributes Demo</h1>
        <p>Hover over the heading to see the tooltip. This paragraph is inside a container with a yellow background.</p>
        <button hidden>Hidden Button</button>
    </div>
</body>
</html>
```
In this example:
- The `<div>` has `id`, `class`, `style`, and `data-*` attributes.
- The `<h1>` uses the `title` attribute.
- The `<button>` element is `hidden` by default.


## Key Characteristics**

### Comparison Table of Common Global Attributes
| Attribute      | Description                                              | Typical Values                 | Example                           |
|----------------|----------------------------------------------------------|--------------------------------|------------------------------------|
| `id`           | Unique identifier                                        | Any valid string               | `id="main-header"`               |
| `class`        | Used for grouping elements for styling or scripting      | Space-separated class names     | `class="highlight main"`         |
| `style`        | Inline CSS styling                                       | CSS declarations               | `style="color:red;"`             |
| `title`        | Advisory text shown on hover                             | Any valid string               | `title="Submit the form"`        |
| `data-*`       | Custom data attributes for scripting                     | `data-info="value"` etc.      | `data-user="12345"`              |
| `hidden`       | Hides the element from display                           | Boolean (presence)             | `hidden`                           |
| `tabindex`     | Allows keyboard navigation focus                         | Numeric order or `-1`          | `tabindex="1"`                   |
| `draggable`    | Makes element draggable (HTML5)                          | `true`, `false`, `auto`        | `draggable="true"`               |
| `spellcheck`   | Toggles spell checking on text fields                    | `true`, `false`                | `spellcheck="true"`              |

### Common Global Attributes**
| Attribute          | Description                                                                 | Example                                                                 |
|---------------------|-----------------------------------------------------------------------------|-------------------------------------------------------------------------|
| `class`             | Assigns one or more CSS classes for styling.                                | `<div class="container">...</div>`                                     |
| `id`                | Provides a unique identifier for an element.                                | `<section id="header">...</section>`                                   |
| `style`             | Applies inline CSS styles.                                                  | `<p style="color: red;">Red Text</p>`                                  |
| `title`             | Adds a tooltip with extra information.                                      | `<abbr title="HyperText Markup Language">HTML</abbr>`                  |
| `lang`              | Specifies the language of the element's content.                            | `<html lang="en">...</html>`                                           |
| `data-*`            | Stores custom data for JavaScript (replace `*` with a name).                | `<div data-user-id="456" data-role="moderator">...</div>`              |
| `hidden`            | Hides the element from rendering (use CSS for visual hiding).               | `<p hidden>This is invisible</p>`                                      |
| `tabindex`          | Controls keyboard navigation order (`0` = focusable, `-1` = not focusable). | `<button tabindex="0">Click Me</button>`                               |
| `contenteditable`   | Makes the element's content editable.                                       | `<div contenteditable>Edit this text!</div>`                           |
| `dir`               | Sets text direction (`ltr`, `rtl`, or `auto`).                              | `<p dir="rtl">مرحبا بالعالم</p>`                                       |
| `accesskey`         | Defines a keyboard shortcut to activate the element.                        | `<button accesskey="s">Save</button>`                                  |
| `draggable`         | Enables drag-and-drop functionality.                                        | `<div draggable="true">Drag me</div>`                                  |
| `spellcheck`        | Toggles browser spell-checking for editable content.                        | `<textarea spellcheck="true"></textarea>`                              |
| `translate`         | Hints whether the content should be translated.                             | `<span translate="no">Brand Name</span>`                               |

### Categories of Global Attributes**
Global attributes can be grouped by purpose:
1. **Styling**: `class`, `style`, `hidden`.
2. **Accessibility**: `lang`, `dir`, `tabindex`, `accesskey`.
3. **Behavior**: `contenteditable`, `draggable`, `spellcheck`.
4. **Metadata**: `id`, `title`, `data-*`, `translate`.

## References & Recommended Resources
1. [MDN Web Docs - Global Attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes)
2. [W3Schools - HTML Global Attributes](https://www.w3schools.com/html/html_attributes.asp)
3. [HTML Living Standard](https://html.spec.whatwg.org/multipage/)

---
## ⭐️ Understanding HTML Image Elements (`<img>`)

## Introduction
The `<img>` element in HTML is used to embed images into a web page. Whether illustrating content, providing additional information, or optimizing user experience, images often play a crucial role in modern web design. Proper use of the `<img>` element is essential for performance, accessibility, and layout.

## What is the `<img>` Element?
The `<img>` element is a **void element** that doesn’t require a closing tag. It includes various attributes to control how images are displayed, loaded, and described.

### Key Characteristics
1. **Void Element**: No closing tag (e.g., `<img src="image.jpg">` is sufficient).
2. **Inline by Default**: The element flows in line with surrounding text unless styled otherwise.
3. **Accessibility**: The `alt` attribute provides alternative text, crucial for screen readers and SEO.
4. **External Resource**: Images are typically hosted as separate files, which the `<img>` element references.

## Basic Syntax
```html
<img src="path/to/image.jpg" alt="Alternative text" />
```

### Common Attributes
- **`src`**: Specifies the image source (URL or relative path).
- **`alt`**: Provides alternative text if the image fails to load or for accessibility.
- **`width`** and **`height`**: Controls the display size (in pixels or percentages) of the image.
- **`title`**: Adds a tooltip on hover.
- **`loading`**: Defines how images should be loaded (`lazy`, `eager`).
- **`decoding`**: Hints for how the browser decodes images (`async`, `sync`).
- **`srcset`** & **`sizes`**: For responsive images, providing multiple sources depending on viewport or device pixel ratio.

### Core Attributes
| Attribute     | Description                                                                 | Required? | Example                                  |
|---------------|-----------------------------------------------------------------------------|-----------|------------------------------------------|
| `src`         | Specifies the image URL (absolute or relative).                             | Yes       | `src="/images/logo.png"`                 |
| `alt`         | Provides descriptive text for accessibility and broken images.              | Yes*      | `alt="Company logo"`                     |
| `width`/`height` | Defines image dimensions (in pixels). Avoids layout shifts during loading. | No        | `width="600" height="400"`               |
| `srcset`      | Offers multiple image sources for responsive design.                        | No        | `srcset="small.jpg 480w, large.jpg 1080w"` |
| `sizes`       | Specifies display sizes for `srcset` images.                                | No        | `sizes="(max-width: 600px) 480px, 1080px"` |
| `loading`     | Controls lazy loading (`lazy` defers offscreen images).                     | No        | `loading="lazy"`                         |
| `decoding`    | Hints how the browser should decode the image (`sync`, `async`, `auto`).    | No        | `decoding="async"`                       |
| `crossorigin` | Enables CORS for images loaded from external domains.                       | No        | `crossorigin="anonymous"`                |

-> The `alt` attribute is required for accessibility but can be empty (`alt=""`) for decorative images.

## Example Usage
### 1. Simple Image
```html
<img src="coffee.jpg" alt="Cup of coffee">
```

### 2. Image with Title
```html
<img src="coffee.jpg" alt="Cup of coffee" title="Morning coffee" />
```

### 3. Specifying Dimensions
```html
<img src="coffee.jpg" alt="Cup of coffee" width="300" height="200" />
```

### 4. Lazy Loading
```html
<img src="coffee.jpg" alt="Cup of coffee" loading="lazy" />
```
- This delays the loading of the image until it’s near the viewport.

### 5. Responsive Image (Using `srcset`)
```html
<img 
  src="images/coffee-400.jpg" 
  alt="Cup of coffee"
  srcset="images/coffee-400.jpg 400w, images/coffee-800.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
>
```
- The browser chooses the most appropriate image size based on viewport and device pixel density.

## Image Formats
1. **JPEG (jpg)**
   - Best for photographs or images with many colors.
   - Uses lossy compression.
2. **PNG**
   - Supports transparency and lossless compression.
   - Suitable for logos, icons, and graphics with fewer colors.
3. **GIF**
   - Supports animation.
   - Limited to 256 colors.
4. **SVG**
   - Vector-based, scales without losing clarity.
   - Ideal for icons, logos, and illustrations.
5. **WebP**
   - Offers superior compression for both lossy and lossless images.
   - Not supported by older browsers, but widespread adoption is growing.
6. **Performance**
- **Optimize formats**:
  | Format   | Best For                        | Pros                            | Cons                  |
  |----------|---------------------------------|---------------------------------|-----------------------|
  | JPEG     | Photos with gradients           | Small file size                 | Lossy compression     |
  | PNG      | Transparency, logos             | Lossless quality                | Larger files          |
  | WebP     | Modern browsers (replaces JPEG) | Superior compression            | Limited browser support |
  | AVIF     | Next-gen compression            | Even smaller than WebP          | Very new standard     |
- Use **CDNs** for faster delivery (e.g., Cloudinary, Imgix).
- **Compress images** with tools like Squoosh or ImageOptim.

## Diagram: `<img>` Element Structure
```plaintext
<img
    src="path/to/image"
    alt="Descriptive alternative text"
    width="x" height="y"
    loading="lazy"
    srcset="..."
    sizes="..."
>
```
1. **`src`**: Image path.
2. **`alt`**: Accessibility.
3. **`width`**, **`height`**: Size control.
4. **`loading`**: Loading strategy.
5. **`srcset`** + **`sizes`**: Responsive image technique.

## Comparison Table of Key Attributes
| Attribute     | Purpose                                                          | Example Value                  |
|---------------|------------------------------------------------------------------|--------------------------------|
| `src`         | Specifies the image file path/URL                                | `"images/photo.jpg"`          |
| `alt`         | Describes the image for accessibility and fallback              | `"Photo of a beach"`          |
| `width`       | Image display width (in px or %)                                 | `300` or `"50%"`               |
| `height`      | Image display height (in px or %)                                | `200` or `"auto"`              |
| `title`       | Tooltip on hover                                                | `"Click to view larger"`       |
| `loading`     | Controls image loading strategy (lazy or eager)                 | `"lazy"`, `"eager"`            |
| `decoding`    | Hints for how browser decodes the image                         | `"sync"`, `"async"`, `"auto"`  |
| `srcset`      | Specifies multiple image versions for responsive design         | `"image-400.jpg 400w, ..."`   |
| `sizes`       | Specifies display size for each media condition in `srcset`     | `"(max-width: 600px) 400px"`  |

## References & Recommended Resources
1. [MDN Web Docs - `<img>` Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)
2. [W3Schools - HTML `<img>`](https://www.w3schools.com/tags/tag_img.asp)
3. [HTML Living Standard](https://html.spec.whatwg.org/multipage/)
4. [Responsive Images Guide](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images)