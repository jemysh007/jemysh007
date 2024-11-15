# jQuery Cheat Sheet

This cheat sheet serves as a quick reference for jQuery functions, syntax, selectors, and utilities.

---

## 1. **Selecting Elements**

### Basic Selector

```javascript
$('#id');  // Select element by ID
$('.class');  // Select elements by class
$('element');  // Select elements by tag name (e.g., 'div', 'p')
```

### Combining Selectors

```javascript
$('#id, .class');  // Select by ID and class
$('p, div');  // Select all <p> and <div> elements
```

### Descendant Selector

```javascript
$('#parent div');  // Select <div> elements inside #parent
$('.container p');  // Select <p> elements inside any .container
```

### Attribute Selector

```javascript
$('input[name="username"]');  // Select <input> elements with the name "username"
$('a[href^="https"]');  // Select <a> elements where href starts with "https"
```

---

## 2. **Events**

### Binding Events

```javascript
$('#button').click(function() {
    alert('Button clicked!');
});

$('#button').hover(
    function() { $(this).css('background', 'red'); },
    function() { $(this).css('background', ''); }
);

$('p').on('click', function() {
    $(this).css('color', 'blue');
});
```

### Mouse Events

```javascript
$('#button').mousedown(function() {
    alert('Mouse button pressed!');
});

$('#button').mouseup(function() {
    alert('Mouse button released!');
});
```

### Keyboard Events

```javascript
$('#input').keypress(function(event) {
    console.log('Key pressed: ' + event.which);
});

$('#input').focus(function() {
    console.log('Input field focused');
});
```

---

## 3. **Manipulating DOM**

### Changing Content

```javascript
$('#element').text('New text content');  // Set text content
$('#element').html('<p>New HTML content</p>');  // Set HTML content
$('#element').val('New value');  // Set value for form elements
```

### Appending & Prepending

```javascript
$('#parent').append('<p>New paragraph</p>');  // Add as the last child
$('#parent').prepend('<p>New paragraph</p>');  // Add as the first child
```

### Removing Elements

```javascript
$('#element').remove();  // Remove element
$('.class').empty();  // Remove all children from an element
```

### Adding/Removing Classes

```javascript
$('#element').addClass('highlight');  // Add class
$('#element').removeClass('highlight');  // Remove class
$('#element').toggleClass('highlight');  // Toggle class
```

### Show/Hide Elements

```javascript
$('#element').show();  // Show element
$('#element').hide();  // Hide element
$('#element').toggle();  // Toggle visibility
```

---

## 4. **CSS Manipulation**

```javascript
$('#element').css('color', 'blue');  // Set CSS property
$('#element').css({
    'color': 'blue',
    'font-size': '20px'
});  // Set multiple CSS properties
```

### Getting CSS Properties

```javascript
let color = $('#element').css('color');  // Get the color CSS property
```

---

## 5. **Animations**

### Fade In/Out

```javascript
$('#element').fadeIn();  // Fade in element
$('#element').fadeOut();  // Fade out element
$('#element').fadeTo(1000, 0.5);  // Fade to specific opacity (0.5)
```

### Slide In/Out

```javascript
$('#element').slideDown();  // Slide down element
$('#element').slideUp();  // Slide up element
$('#element').slideToggle();  // Slide toggle element
```

### Custom Animation

```javascript
$('#element').animate({
    left: '100px',
    opacity: 0.5
}, 1000);  // Move and animate opacity
```

---

## 6. **AJAX**

### Basic AJAX Request

```javascript
$.ajax({
    url: 'https://api.example.com/data',
    type: 'GET',
    success: function(response) {
        console.log(response);
    },
    error: function(xhr, status, error) {
        console.error(error);
    }
});
```

### Load Method (Simplified AJAX)

```javascript
$('#content').load('page.html');  // Load content from page.html into #content
```

### Get and Post Methods

```javascript
$.get('data.json', function(response) {
    console.log(response);
});

$.post('submit.php', { name: 'John', age: 25 }, function(response) {
    console.log(response);
});
```

---

## 7. **Traversing DOM**

### Parent, Child, and Sibling Traversal

```javascript
$('#child').parent();  // Select the parent element
$('#child').children();  // Select all child elements
$('#child').siblings();  // Select all siblings
```

### Finding Specific Elements

```javascript
$('#parent').find('p');  // Find all <p> elements inside #parent
```

### Filtering Elements

```javascript
$('.items').filter('.active');  // Find elements with both 'items' and 'active' classes
$('.items').not('.active');  // Find elements that do not have the 'active' class
```

---

## 8. **Form Manipulation**

### Get & Set Form Values

```javascript
let username = $('#username').val();  // Get input value
$('#username').val('newUsername');  // Set input value
```

### Form Submit

```javascript
$('#form').submit(function(event) {
    event.preventDefault();  // Prevent default form submission
    console.log('Form submitted');
});
```

### Checkboxes & Radio Buttons

```javascript
$('#checkbox').prop('checked', true);  // Check a checkbox
let isChecked = $('#checkbox').prop('checked');  // Check if a checkbox is checked
```

---

## 9. **Utilities**

### Get Document Ready

```javascript
$(document).ready(function() {
    // Code to run when the DOM is fully loaded
});
```

Or simply:

```javascript
$(function() {
    // Code to run when the DOM is fully loaded
});
```

### Set Timeout and Interval

```javascript
setTimeout(function() {
    console.log('Executed after 3 seconds');
}, 3000);

let interval = setInterval(function() {
    console.log('This runs every 2 seconds');
}, 2000);

clearInterval(interval);  // Stop the interval
```

---

## 10. **Chaining Methods**

You can chain multiple jQuery methods together to perform multiple actions in one line.

```javascript
$('#element').css('color', 'red').slideUp().fadeIn().text('New text');
```

---

## Conclusion

This jQuery cheat sheet provides a quick reference to common jQuery syntax, functions, and methods for DOM manipulation, event handling, AJAX requests, and more. Keep this handy as a guide for your jQuery projects!
