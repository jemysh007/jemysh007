## Step-by-Step Guide to Integrate Animate.css & WOW.js Using CDN

### 1. **Include Animate.css**

Animate.css is a library of cross-browser animations that you can apply to elements using CSS classes.

#### CDN Link for Animate.css:

Add the following link in the `<head>` section of your HTML document to include Animate.css.

```html
<head>
  <!-- Animate.css CDN -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">
</head>
```

### 2. **Include WOW.js**

WOW.js is a JavaScript library that reveals animations when the user scrolls down the page. It adds animation classes to the elements as they come into the viewport.

#### CDN Link for WOW.js:

Add the following scripts at the end of your HTML document (just before the closing `</body>` tag).

```html
<body>
  <!-- Your page content here -->

  <!-- WOW.js CDN -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/wow/1.1.2/wow.min.js"></script>

  <script>
    // Initialize WOW.js
    new WOW().init();
  </script>
</body>
```

### 3. **Using Animate.css and WOW.js Together**

Now that both libraries are included, we can create an example where elements animate on scroll using **WOW.js** and **Animate.css**.

#### Example HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Animate.css and WOW.js Example</title>

  <!-- Animate.css CDN -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css">

  <!-- WOW.js CDN -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/wow/1.1.2/wow.min.js"></script>
</head>
<body>

  <div class="container">
    <h1 class="wow animate__animated animate__fadeIn">Hello, World!</h1>
    <p class="wow animate__animated animate__bounceInUp">This is an animated paragraph using Animate.css and WOW.js.</p>

    <div class="box wow animate__animated animate__zoomIn" style="height: 200px; background-color: lightblue; margin-top: 20px;">
      This box will animate when scrolled into view.
    </div>
  </div>

  <!-- Initialize WOW.js -->
  <script>
    new WOW().init();
  </script>

</body>
</html>
```

### 4. **Explanation of the Code:**

- **`<link>` to Animate.css:** This link imports the Animate.css library, which contains all the CSS animations.
- **`<script>` to WOW.js:** This script imports WOW.js, which will add the animations when elements come into the viewport.
- **Classes used:**
  - **`wow`**: This class is necessary for WOW.js to identify elements that should be animated on scroll.
  - **`animate__animated`**: This is a general class used by Animate.css to apply animations.
  - **Animation classes (`animate__fadeIn`, `animate__bounceInUp`, `animate__zoomIn`)**: These classes apply specific animations to the elements.

### 5. **Additional Notes:**

- You can customize the animations by adding more Animate.css classes like `animate__fadeIn`, `animate__zoomIn`, `animate__slideInUp`, etc.
- WOW.js will only trigger animations when the elements scroll into view, ensuring that animations are not played as soon as the page loads but when they become visible.
- You can adjust the animation trigger points (e.g., when elements are 50% in the viewport) by customizing WOW.js options in the initialization.

#### Example Customization:

If you want to tweak the settings, you can pass options to the `WOW()` constructor.

```javascript
new WOW({
  offset: 100,           // Trigger animation when the element is 100px in the viewport
  mobile: true,          // Enable animations on mobile devices
  live: true             // Enables dynamic content animation
}).init();
```

### 6. **CDN Links Summary:**

- **Animate.css CDN:** `https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css`
- **WOW.js CDN:** `https://cdnjs.cloudflare.com/ajax/libs/wow/1.1.2/wow.min.js`

---

By following this documentation, you can easily integrate both **Animate.css** for animations and **WOW.js** for scroll-triggered animations into your project with just a few lines of code.