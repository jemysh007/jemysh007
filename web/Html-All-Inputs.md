
# Documentation: Retrieving Input Values in JavaScript

This document explains how to use JavaScript to retrieve values from different input types in an HTML form by their `id`. 

## **Input Types and Retrieval Methods**

### **1. Text Input**
- **HTML Code**:
  ```html
  <input type="text" id="textInput">
  ```
- **JavaScript Code**:
  ```javascript
  const textValue = document.getElementById('textInput').value;
  ```
- **Explanation**:
  Retrieves the value entered in the text input field.

---

### **2. Email Input**
- **HTML Code**:
  ```html
  <input type="email" id="emailInput">
  ```
- **JavaScript Code**:
  ```javascript
  const emailValue = document.getElementById('emailInput').value;
  ```
- **Explanation**:
  Retrieves the email entered by the user. This field expects a valid email format.

---

### **3. Password Input**
- **HTML Code**:
  ```html
  <input type="password" id="passwordInput">
  ```
- **JavaScript Code**:
  ```javascript
  const passwordValue = document.getElementById('passwordInput').value;
  ```
- **Explanation**:
  Retrieves the text entered in the password input field.

---

### **4. Number Input**
- **HTML Code**:
  ```html
  <input type="number" id="numberInput">
  ```
- **JavaScript Code**:
  ```javascript
  const numberValue = document.getElementById('numberInput').value;
  ```
- **Explanation**:
  Retrieves the number entered in the input field.

---

### **5. Date Input**
- **HTML Code**:
  ```html
  <input type="date" id="dateInput">
  ```
- **JavaScript Code**:
  ```javascript
  const dateValue = document.getElementById('dateInput').value;
  ```
- **Explanation**:
  Retrieves the selected date in `YYYY-MM-DD` format.

---

### **6. Radio Button**
- **HTML Code**:
  ```html
  <input type="radio" id="radio1" name="radioInput" value="Option 1">
  <input type="radio" id="radio2" name="radioInput" value="Option 2">
  ```
- **JavaScript Code**:
  ```javascript
  const radioValue = document.querySelector('input[name="radioInput"]:checked')?.value || null;
  ```
- **Explanation**:
  Retrieves the value of the selected radio button. If none is selected, it returns `null`.

---

### **7. Checkbox**
- **HTML Code**:
  ```html
  <input type="checkbox" id="checkbox1" value="Option A">
  <input type="checkbox" id="checkbox2" value="Option B">
  ```
- **JavaScript Code**:
  ```javascript
  const checkboxValues = Array.from(document.querySelectorAll('input[type="checkbox"]:checked')).map(cb => cb.value);
  ```
- **Explanation**:
  Retrieves all selected checkbox values as an array. If no checkboxes are selected, it returns an empty array.

---

### **8. Dropdown (Select)**
- **HTML Code**:
  ```html
  <select id="dropdownInput">
    <option value="Option 1">Option 1</option>
    <option value="Option 2">Option 2</option>
  </select>
  ```
- **JavaScript Code**:
  ```javascript
  const dropdownValue = document.getElementById('dropdownInput').value;
  ```
- **Explanation**:
  Retrieves the selected value from the dropdown menu.

---

### **9. Textarea**
- **HTML Code**:
  ```html
  <textarea id="textareaInput"></textarea>
  ```
- **JavaScript Code**:
  ```javascript
  const textareaValue = document.getElementById('textareaInput').value;
  ```
- **Explanation**:
  Retrieves the text entered in the textarea field.

---

## **Example: Complete Script**
Here is an example that retrieves values from all the input types in a form:

```javascript
function submitForm() {
  const data = {
    textInput: document.getElementById('textInput').value,
    emailInput: document.getElementById('emailInput').value,
    passwordInput: document.getElementById('passwordInput').value,
    numberInput: document.getElementById('numberInput').value,
    dateInput: document.getElementById('dateInput').value,
    radioInput: document.querySelector('input[name="radioInput"]:checked')?.value || null,
    checkboxInput: Array.from(document.querySelectorAll('input[type="checkbox"]:checked')).map(cb => cb.value),
    dropdownInput: document.getElementById('dropdownInput').value,
    textareaInput: document.getElementById('textareaInput').value
  };

  console.log(data);
  alert('Form data submitted! Check the console for details.');
}
```

---

## **How to Use**
1. Add the HTML form elements to your webpage with the specified `id` attributes.
2. Use the corresponding JavaScript snippet to retrieve values from the inputs.
3. The collected data can be logged or sent to a server for further processing.

---

This documentation provides a clear reference for working with various input types in HTML and collecting their values using JavaScript.
