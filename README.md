# Calculator
Learning React - The calculator from: https://www.youtube.com/watch?v=h6lVvsUkdjI&amp;ab_channel=CodeWithYousaf

This simple calculator can be used to learn React, javascript, and CSS.

### Code Explanation:
fyi: this was made using chat GPT, I like how it described the components.

The provided React code is a simple calculator application with buttons for numbers, operators, and functions like "AC" (All Clear), "DE" (Delete), and "=" (Evaluate). Here's what each part of the code does:

---

### 1. **State Management with `useState`**
```jsx
const [value, setValue] = useState("");
```
- `value`: Holds the current input or result displayed on the calculator.
- `setValue`: Updates the `value` state.
- Initially set to an empty string (`""`).

---

### 2. **Rendering the Calculator Layout**
The calculator is rendered using HTML-like JSX elements:
```jsx
<div className="container">
  <div className="calculator">
    <form action="">
```
- `container` and `calculator`: CSS classes define the styling.
- A `form` wraps the calculator but doesn't submit any data.

---

### 3. **Display Section**
```jsx
<div className="display">
  <input type="text" value={value} />
</div>
```
- Displays the current input or result.
- The `value` attribute is bound to the `value` state, making this a **controlled component**.

---

### 4. **Button Functionalities**
Each button has an `onClick` event that updates the `value` state based on its functionality:

#### a. **"AC" Button**
```jsx
<input type="button" value="AC" onClick={(e) => setValue("")} />
```
- Clears the input by resetting `value` to an empty string.

#### b. **"DE" Button**
```jsx
<input type="button" value="DE" onClick={(e) => setValue(value.slice(0, -1))} />
```
- Deletes the last character of `value` using `slice`.

#### c. **Number and Operator Buttons**
```jsx
<input
  type="button"
  value="7"
  onClick={(e) => setValue(value + e.target.value)}
/>
```
- Appends the button's value (retrieved via `e.target.value`) to the current `value`.

#### d. **"=" Button**
```jsx
<input
  type="button"
  value="="
  className="equal"
  onClick={(e) => setValue(eval(value))}
/>
```
- Evaluates the mathematical expression in `value` using the JavaScript `eval()` function.
- Example: If `value` is `"3+5"`, clicking "=" sets `value` to `"8"`.

**⚠️ Warning:** Using `eval()` is potentially unsafe if untrusted user input is allowed. Consider alternatives like a math expression parser for production apps.

---

### 5. **Grouping Buttons**
Buttons are grouped using `<div>` elements to organize numbers and operators visually:
```jsx
<div>
  <input type="button" value="1" onClick={(e) => setValue(value + e.target.value)} />
  <input type="button" value="2" onClick={(e) => setValue(value + e.target.value)} />
  ...
</div>
```

---

### 6. **Styling**
The `container` and `calculator` are styled through CSS in the linked `App.css`. The layout and button design are likely defined here.

---

### Summary of Functionalities:
- **Clear (AC):** Resets the input.
- **Delete (DE):** Removes the last character.
- **Input Numbers/Operators:** Adds the button's value to the input.
- **Evaluate (=):** Computes the mathematical result.

This structure allows you to extend the calculator further, adding features like memory storage or error handling for invalid inputs.
