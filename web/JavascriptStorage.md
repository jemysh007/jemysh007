Here’s the combined Markdown document including all the code for the four files:

```markdown
# File Descriptions with Code

This document provides a brief explanation of four HTML files that demonstrate the usage of `localStorage` and `sessionStorage` in JavaScript, along with the complete code for each file.

---

## File: localstorage.html

This file is an HTML document that provides a simple form for capturing a user's name and storing it in the browser's `localStorage`. Upon submission, it redirects the user to another page (`localstorage2.html`).

### Key Features:
- Input field for the user's name.
- Button that triggers the `submit()` function.
- `submit()` function:
  - Retrieves the input value.
  - Stores the value in `localStorage` under the key `myName`.
  - Redirects the user to `localstorage2.html`.

### Code:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <input type="text" id="name" placeholder="Enter Name">
    <button onclick="submit()">Submit</button>
    <script>
        function submit() {
            const name = document.getElementById("name").value;
            
            localStorage.setItem("myName", name);

            window.location.href = "localstorage2.html";
        }
    </script>
</body>
</html>
```

---

## File: localstorage2.html

This file is an HTML document that retrieves and displays the user's name stored in `localStorage` by the previous page (`localstorage.html`).

### Key Features:
- Displays a welcome message with the user's name.
- JavaScript:
  - Retrieves the value of `myName` from `localStorage`.
  - Updates the `<p>` element with the retrieved name.

### Code:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    Welcome <p id="name"></p>

    <script>
        var name = localStorage.getItem("myName")

        document.querySelector("#name").innerHTML = name    
    </script>
</body>
</html>
```

---

## File: sessionstorage.html

This file is an HTML document that allows the user to input their email and stores it in the browser's `sessionStorage`. After submission, it redirects the user to another page (`sessionstorage2.html`).

### Key Features:
- Input field for the user's email.
- Button that triggers the `submit()` function.
- `submit()` function:
  - Retrieves the input value.
  - Stores the value in `sessionStorage` under the key `email`.
  - Redirects the user to `sessionstorage2.html`.

### Code:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <input type="text" id="name" placeholder="Enter Email">
    <button onclick="submit()">Submit</button>
    <script>
        function submit() {
            const name = document.getElementById("name").value;
            
            sessionStorage.setItem("email", name);

            window.location.href = "sessionstorage2.html";
        }
    </script>
</body>
</html>
```

---

## File: sessionstorage2.html

This file is an HTML document that retrieves and displays the user's email stored in `sessionStorage` by the previous page (`sessionstorage.html`).

### Key Features:
- Displays a welcome message with the user's email.
- JavaScript:
  - Retrieves the value of `email` from `sessionStorage`.
  - Updates the `<p>` element with the retrieved email.

### Code:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    Welcome <p id="name"></p>

    <script>
        var name = sessionStorage.getItem("email")

        document.querySelector("#name").innerHTML = name    
    </script>
</body>
</html>
```
```

