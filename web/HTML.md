# HTML

This cheat sheet contains all the essential HTML elements, attributes, and their usage, providing quick references for HTML structure and syntax.

## 1. **HTML Document Structure**

An HTML document structure includes a declaration, root element, metadata, and content elements.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

---

## 2. **Text Elements**

### Paragraph

```html
<p>This is a paragraph of text.</p>
```

### Heading

```html
<h1>This is a Heading 1</h1>
<h2>This is a Heading 2</h2>
<h3>This is a Heading 3</h3>
<h4>This is a Heading 4</h4>
<h5>This is a Heading 5</h5>
<h6>This is a Heading 6</h6>
```

### Line Break

```html
<p>This is a paragraph.<br>This is a new line.</p>
```

### Bold Text

```html
<b>This text is bold.</b>
```

### Italic Text

```html
<i>This text is italic.</i>
```

### Strong Text

```html
<strong>This is important text.</strong>
```

### Emphasized Text

```html
<em>This is emphasized text.</em>
```

### Marked Text

```html
<mark>This text is highlighted.</mark>
```

### Deleted Text

```html
<del>This text has been deleted.</del>
```

### Inserted Text

```html
<ins>This text has been inserted.</ins>
```

### Subscript Text

```html
<sub>This is subscript text.</sub>
```

### Superscript Text

```html
<sup>This is superscript text.</sup>
```

---

## 3. **Links**

### Anchor Link

```html
<a href="https://www.example.com">Visit Example</a>
```

### Link with a Target

```html
<a href="https://www.example.com" target="_blank">Open Example in a New Tab</a>
```

---

## 4. **Lists**

### Unordered List

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

### Ordered List

```html
<ol>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>
```

### Definition List

```html
<dl>
    <dt>HTML</dt>
    <dd>Hypertext Markup Language</dd>
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
</dl>
```

---

## 5. **Forms**

### Basic Form

```html
<form action="/submit" method="POST">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    <br><br>
    <input type="submit" value="Submit">
</form>
```

### Input Types

```html
<input type="text" placeholder="Text">
<input type="password" placeholder="Password">
<input type="email" placeholder="Email">
<input type="number" placeholder="Number">
<input type="date">
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female
<input type="checkbox" name="subscribe" value="yes"> Subscribe
```

### Textarea

```html
<textarea rows="4" cols="50" placeholder="Enter text here"></textarea>
```

### Select Dropdown

```html
<select name="fruit">
    <option value="apple">Apple</option>
    <option value="banana">Banana</option>
    <option value="cherry">Cherry</option>
</select>
```

---

## 6. **Media Elements**

### Image

```html
<img src="image.jpg" alt="A descriptive text" width="500" height="300">
```

### Audio

```html
<audio controls>
    <source src="audio.mp3" type="audio/mp3">
    Your browser does not support the audio element.
</audio>
```

### Video

```html
<video controls width="600">
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>
```

---

## 7. **Tables**

### Table Structure

```html
<table>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Row 1, Cell 1</td>
            <td>Row 1, Cell 2</td>
        </tr>
        <tr>
            <td>Row 2, Cell 1</td>
            <td>Row 2, Cell 2</td>
        </tr>
    </tbody>
</table>
```

---

## 8. **Semantic HTML5 Elements**

### Header

```html
<header>
    <h1>Website Header</h1>
</header>
```

### Footer

```html
<footer>
    <p>&copy; 2024 My Website</p>
</footer>
```

### Article

```html
<article>
    <h2>Article Title</h2>
    <p>This is the article content.</p>
</article>
```

### Section

```html
<section>
    <h2>Section Title</h2>
    <p>This is the content of the section.</p>
</section>
```

### Nav

```html
<nav>
    <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#services">Services</a></li>
    </ul>
</nav>
```

### Aside

```html
<aside>
    <h3>Related Articles</h3>
    <ul>
        <li><a href="#">Article 1</a></li>
        <li><a href="#">Article 2</a></li>
    </ul>
</aside>
```

---

## 9. **Embedding Content**

### iframe

```html
<iframe src="https://www.example.com" width="600" height="400"></iframe>
```

### Embed (for other content types like PDF, Flash, etc.)

```html
<embed src="file.pdf" width="600" height="400">
```

### Object (for Flash or other media files)

```html
<object data="movie.swf" type="application/x-shockwave-flash" width="400" height="300"></object>
```

---

## 10. **Meta Tags for SEO and Responsiveness**

### Meta Charset

```html
<meta charset="UTF-8">
```

### Meta Viewport for Responsiveness

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Meta Description

```html
<meta name="description" content="A short description of the page for SEO purposes.">
```

### Meta Keywords

```html
<meta name="keywords" content="HTML, CSS, JavaScript, Web Development">
```

---

## 11. **Adding CSS to HTML**

You can add CSS to an HTML document in three ways:

### Inline CSS

```html
<p style="color: red;">This text is red.</p>
```

### Internal CSS (within `<style>` tag)

```html
<head>
    <style>
        p {
            color: blue;
        }
    </style>
</head>
```

### External CSS (linking to an external stylesheet)

```html
<head>
    <link rel="stylesheet" href="styles.css">
</head>
```

---

## 12. **Adding JavaScript to HTML**

You can add JavaScript to an HTML document in two main ways:

### Inline JavaScript

```html
<button onclick="alert('Hello World!')">Click Me</button>
```

### External JavaScript (linking to an external script)

```html
<head>
    <script src="script.js"></script>
</head>
```

### Internal JavaScript (within `<script>` tag)

```html
<script>
    console.log('Hello World!');
</script>
```

---

## Conclusion

This cheat sheet provides a quick reference to commonly used HTML elements. It's designed to help you get started or quickly find syntax for various HTML tags and attributes.

