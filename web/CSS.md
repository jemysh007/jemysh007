# CSS Cheat Sheet

This cheat sheet provides a quick reference to common CSS properties, selectors, and syntax to help you style HTML elements efficiently.

---

## 1. **CSS Syntax**

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

### Universal Selector

```css
* {
    margin: 0;
    padding: 0;
}
```

### Element Selector

```css
h1 {
    color: red;
}
```

### Class Selector

```css
.container {
    max-width: 1200px;
    margin: 0 auto;
}
```

### ID Selector

```css
#header {
    background-color: darkblue;
    color: white;
}
```

### Attribute Selector

```css
input[type="text"] {
    border: 1px solid gray;
}
```

### Descendant Selector

```css
nav a {
    color: white;
}
```

### Child Selector

```css
ul > li {
    list-style: none;
}
```

### Adjacent Sibling Selector

```css
h1 + p {
    margin-top: 0;
}
```

---

## 3. **Colors**

### Color by Name

```css
color: red;
```

### Hexadecimal Color

```css
color: #FF5733;
```

### RGB Color

```css
color: rgb(255, 87, 51);
```

### RGBA (with opacity)

```css
color: rgba(255, 87, 51, 0.5);
```

### HSL Color

```css
color: hsl(9, 100%, 60%);
```

---

## 4. **Text Properties**

### Font Family

```css
font-family: 'Arial', sans-serif;
```

### Font Size

```css
font-size: 16px;
```

### Font Weight

```css
font-weight: bold;
```

### Text Align

```css
text-align: center;
```

### Text Transform

```css
text-transform: uppercase;
```

### Text Decoration

```css
text-decoration: underline;
```

### Line Height

```css
line-height: 1.5;
```

### Letter Spacing

```css
letter-spacing: 1px;
```

---

## 5. **Box Model**

### Width and Height

```css
width: 100%;
height: 200px;
```

### Padding

```css
padding: 10px;
padding-top: 20px;
padding-left: 15px;
```

### Margin

```css
margin: 10px;
margin-bottom: 20px;
margin-right: 15px;
```

### Border

```css
border: 2px solid black;
border-radius: 5px;
```

### Box Sizing

```css
box-sizing: border-box;
```

---

## 6. **Positioning**

### Static Position (default)

```css
position: static;
```

### Relative Position

```css
position: relative;
top: 10px;
left: 20px;
```

### Absolute Position

```css
position: absolute;
top: 50px;
right: 20px;
```

### Fixed Position

```css
position: fixed;
top: 0;
left: 0;
```

### Sticky Position

```css
position: sticky;
top: 0;
```

---

## 7. **Flexbox Layout**

### Flex Container

```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### Justify Content

```css
justify-content: flex-start; /* start */
justify-content: center; /* center */
justify-content: space-between; /* space between */
```

### Align Items

```css
align-items: stretch; /* stretch */
align-items: center; /* center */
align-items: flex-end; /* flex-end */
```

### Flex Direction

```css
flex-direction: row; /* default */
flex-direction: column;
```

---

## 8. **Grid Layout**

### Grid Container

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
}
```

### Grid Item

```css
.item {
    grid-column: span 2;
}
```

---

## 9. **Display Property**

### Block Level

```css
display: block;
```

### Inline Element

```css
display: inline;
```

### Inline Block

```css
display: inline-block;
```

### Flexbox

```css
display: flex;
```

### Grid

```css
display: grid;
```

### None (hide element)

```css
display: none;
```

---

## 10. **Backgrounds**

### Background Color

```css
background-color: #ffcc00;
```

### Background Image

```css
background-image: url('image.jpg');
```

### Background Size

```css
background-size: cover; /* cover the entire element */
background-size: contain; /* contains the whole image */
```

### Background Position

```css
background-position: center;
background-position: top right;
```

### Background Repeat

```css
background-repeat: no-repeat;
background-repeat: repeat;
```

---

## 11. **CSS Transitions and Animations**

### Transition

```css
transition: all 0.3s ease-in-out;
```

### Hover Effect

```css
button:hover {
    background-color: blue;
}
```

### Animation

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

### Mobile-First Design

```css
@media screen and (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```

### Target Specific Devices

```css
@media screen and (min-width: 600px) {
    .container {
        max-width: 800px;
    }
}
```

---

## 13. **CSS Variables**

### Defining Variables

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

### Hover State

```css
a:hover {
    color: red;
}
```

### Active State

```css
a:active {
    color: blue;
}
```

### Focus State

```css
input:focus {
    border-color: green;
}
```

### First-child

```css
ul li:first-child {
    font-weight: bold;
}
```

### Last-child

```css
ul li:last-child {
    color: blue;
}
```

---

## Conclusion

This CSS cheat sheet covers most commonly used CSS properties, values, and selectors to style your HTML documents effectively. Keep this reference handy to speed up your development process and make styling easier!