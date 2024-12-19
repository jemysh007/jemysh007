# CSS Cheat Sheet

This cheat sheet provides a quick reference to common CSS properties, selectors, and syntax to help you style HTML elements efficiently.

---

## 1. **CSS Syntax**

CSS syntax consists of a selector and a declaration block. The selector points to the HTML element you want to style. The declaration block contains one or more declarations separated by semicolons. Each declaration includes a CSS property name and a value, separated by a colon.

```css
selector {
    property: value;
}
```

Example:

```css
body {
    background-color: lightblue;
    font-family: Arial, sans-serif;
}
```

---

## 2. **Selectors**

Selectors are used to target HTML elements for styling.

### Universal Selector

The universal selector (*) selects all elements on the page.

```css
* {
    margin: 0;
    padding: 0;
}
```

### Element Selector

The element selector selects all elements of a given type.

```css
h1 {
    color: red;
}
```

### Class Selector

The class selector selects all elements with a specific class attribute.

```css
.container {
    max-width: 1200px;
    margin: 0 auto;
}
```

### ID Selector

The ID selector selects a single element with a specific ID attribute.

```css
#header {
    background-color: darkblue;
    color: white;
}
```

### Attribute Selector

The attribute selector selects elements with a specific attribute and value.

```css
input[type="text"] {
    border: 1px solid gray;
}
```

### Descendant Selector

The descendant selector selects elements that are descendants of another element.

```css
nav a {
    color: white;
}
```

### Child Selector

The child selector selects elements that are direct children of another element.

```css
ul > li {
    list-style: none;
}
```

### Adjacent Sibling Selector

The adjacent sibling selector selects an element that is immediately preceded by another element.

```css
h1 + p {
    margin-top: 0;
}
```

---

## 3. **Colors**

CSS allows you to set colors using different formats.

### Color by Name

You can use predefined color names.

```css
color: red;
```

### Hexadecimal Color

Hexadecimal colors are specified with a hash symbol (#) followed by six hex digits.

```css
color: #FF5733;
```

### RGB Color

RGB colors are specified with the rgb() function, which takes three comma-separated values for red, green, and blue.

```css
color: rgb(255, 87, 51);
```

### RGBA (with opacity)

RGBA colors are like RGB colors but with an additional alpha value for opacity.

```css
color: rgba(255, 87, 51, 0.5);
```

### HSL Color

HSL colors are specified with the hsl() function, which takes three values for hue, saturation, and lightness.

```css
color: hsl(9, 100%, 60%);
```

---

## 4. **Text Properties**

Text properties allow you to control the appearance of text.

### Font Family

Sets the font family for text.

```css
font-family: 'Arial', sans-serif;
```

### Font Size

Sets the size of the font.

```css
font-size: 16px;
```

### Font Weight

Sets the weight (boldness) of the font.

```css
font-weight: bold;
```

### Text Align

Sets the horizontal alignment of text.

```css
text-align: center;
```

### Text Transform

Controls the capitalization of text.

```css
text-transform: uppercase;
```

### Text Decoration

Adds decoration to text, such as underlining.

```css
text-decoration: underline;
```

### Line Height

Sets the height of lines of text.

```css
line-height: 1.5;
```

### Letter Spacing

Sets the space between characters.

```css
letter-spacing: 1px;
```

---

## 5. **Box Model**

The box model describes the rectangular boxes generated for elements in the document tree and consists of margins, borders, padding, and the actual content.

### Width and Height

Sets the width and height of an element.

```css
width: 100%;
height: 200px;
```

### Padding

Sets the padding space inside an element.

```css
padding: 10px;
padding-top: 20px;
padding-left: 15px;
```

### Margin

Sets the margin space outside an element.

```css
margin: 10px;
margin-bottom: 20px;
margin-right: 15px;
```

### Border

Sets the border around an element.

```css
border: 2px solid black;
border-radius: 5px;
```

### Box Sizing

Controls how the total width and height of an element are calculated.

```css
box-sizing: border-box;
```

---

## 6. **Positioning**

CSS positioning properties allow you to position an element in the document.

### Static Position (default)

The element is positioned according to the normal flow of the document.

```css
position: static;
```

### Relative Position

The element is positioned relative to its normal position.

```css
position: relative;
top: 10px;
left: 20px;
```

### Absolute Position

The element is positioned relative to its nearest positioned ancestor.

```css
position: absolute;
top: 50px;
right: 20px;
```

### Fixed Position

The element is positioned relative to the browser window.

```css
position: fixed;
top: 0;
left: 0;
```

### Sticky Position

The element is positioned based on the user's scroll position.

```css
position: sticky;
top: 0;
```

---

## 7. **Flexbox Layout**

Flexbox is a layout model that allows you to design complex layouts with ease.

### Flex Container

Defines a flex container and enables flex context for all its direct children.

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### Justify Content

Aligns flex items along the main axis.

```css
justify-content: flex-start; /* start */
justify-content: center; /* center */
justify-content: space-between; /* space between */
```

### Align Items

Aligns flex items along the cross axis.

```css
align-items: stretch; /* stretch */
align-items: center; /* center */
align-items: flex-end; /* flex-end */
```

### Flex Direction

Defines the direction of the main axis.

```css
flex-direction: row; /* default */
flex-direction: column;
```

---

## 8. **Grid Layout**

Grid layout is a powerful layout system for creating complex web layouts.

### Grid Container

Defines a grid container and establishes a new grid formatting context for its contents.

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}
```

### Grid Item

Defines how a grid item is placed in the grid.

```css
.item {
    grid-column: span 2;
}
```

---

## 9. **Display Property**

The display property specifies the display behavior of an element.

### Block Level

The element is displayed as a block.

```css
display: block;
```

### Inline Element

The element is displayed as an inline element.

```css
display: inline;
```

### Inline Block

The element is displayed as an inline-level block container.

```css
display: inline-block;
```

### Flexbox

The element is displayed as a flex container.

```css
display: flex;
```

### Grid

The element is displayed as a grid container.

```css
display: grid;
```

### None (hide element)

The element is not displayed.

```css
display: none;
```

---

## 10. **Backgrounds**

CSS background properties are used to define the background effects for elements.

### Background Color

Sets the background color of an element.

```css
background-color: #ffcc00;
```

### Background Image

Sets the background image of an element.

```css
background-image: url('image.jpg');
```

### Background Size

Specifies the size of the background image.

```css
background-size: cover; /* cover the entire element */
background-size: contain; /* contains the whole image */
```

### Background Position

Specifies the position of the background image.

```css
background-position: center;
background-position: top right;
```

### Background Repeat

Specifies if/how the background image is repeated.

```css
background-repeat: no-repeat;
background-repeat: repeat;
```

---

## 11. **CSS Transitions and Animations**

CSS transitions and animations allow you to create smooth and visually appealing effects.

### Transition

Defines the transition effect for an element.

```css
transition: all 0.3s ease-in-out;
```

### Hover Effect

Changes the style of an element when the user hovers over it.

```css
button:hover {
    background-color: blue;
}
```

### Animation

Defines keyframes and applies animation to an element.

```css
@keyframes slideIn {
    from {
        transform: translateX(-100%);
    }
    to {
        transform: translateX(0);
    }
}

.element {
    animation: slideIn 0.5s ease-out;
}
```

---

## 12. **Media Queries**

Media queries allow you to apply CSS rules based on the characteristics of the device.

### Mobile-First Design

Applies styles for devices with a maximum width of 768px.

```css
@media screen and (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```

### Target Specific Devices

Applies styles for devices with a minimum width of 600px.

```css
@media screen and (min-width: 600px) {
    .container {
        max-width: 800px;
    }
}
```

---

## 13. **CSS Variables**

CSS variables allow you to store values that you can reuse throughout your CSS.

### Defining Variables

Defines custom properties (variables) and uses them in your CSS.

```css
:root {
    --main-bg-color: lightgreen;
    --main-text-color: darkgreen;
}

body {
    background-color: var(--main-bg-color);
    color: var(--main-text-color);
}
```

---

## 14. **Pseudo-Classes**

Pseudo-classes are used to define the special states of an element.

### Hover State

Styles an element when the user hovers over it.

```css
a:hover {
    color: red;
}
```

### Active State

Styles an element when it is activated.

```css
a:active {
    color: blue;
}
```

### Focus State

Styles an element when it has focus.

```css
input:focus {
    border-color: green;
}
```

### First-child

Styles the first child element.

```css
ul li:first-child {
    font-weight: bold;
}
```

### Last-child

Styles the last child element.

```css
ul li:last-child {
    color: blue;
}
```

---

## Conclusion

This CSS cheat sheet covers most commonly used CSS properties, values, and selectors to style your HTML documents effectively. Keep this reference handy to speed up your development process and make styling easier!