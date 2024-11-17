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

The code snippet you provided defines a function `handleEqual` that is responsible for safely evaluating the mathematical expression entered by the user when they press the "=" button on the calculator. Here's a breakdown of each part:

### b.1. **Function Definition**

```javascript
const handleEqual = () => {
```

This defines a function called `handleEqual`. It doesn't take any parameters but uses the state `value` that stores the current mathematical expression.

### b.2. **Try-Catch Block**

```javascript
try {
  setValue(evaluate(value).toString());
} catch (error) {
  setValue("Error");
}
```

- **`try` block**: The code inside the `try` block attempts to evaluate the mathematical expression stored in `value` (e.g., `"3+5*2"`). Here's what happens in the `try` block:

  - `evaluate(value)` is a function from the `math.js` library. It parses the string `value` and computes the result of the mathematical expression. For example, if `value = "3+5*2"`, `evaluate("3+5*2")` will return `13`.
  - `.toString()` converts the result back to a string, which is then set as the new state using `setValue()`.

- **`catch` block**: If the `evaluate` function throws an error (for example, if the user entered an invalid expression like `"3++5"`), the code inside the `catch` block will run. It sets the state `value` to `"Error"`, which will display the string `"Error"` on the screen, indicating that something went wrong.

### b.3. **State Management with `setValue`**

`setValue` is the function from React's `useState` hook used to update the state. In this case, it's updating the `value` that is bound to the input field where the user sees the result of their calculations.

- If the expression is valid, `setValue(evaluate(value).toString())` updates the input with the result of the calculation.
- If the expression is invalid and an error occurs, `setValue("Error")` updates the input with the string "Error".

### b.4. **Why Use `evaluate` from `math.js`?**

- The `evaluate` function from the `math.js` library is safer than using `eval()` because it only evaluates mathematical expressions, preventing the execution of arbitrary code. This is important for preventing security risks like code injection.

### b.5. Full Explanation of the Workflow

1. When the "=" button is clicked, the `handleEqual` function is triggered.
2. It attempts to evaluate the current expression (stored in `value`).
3. If the expression is valid, it computes the result and updates the input field to show the result.
4. If the expression is invalid, it catches the error and sets the input to "Error", providing feedback to the user.

### b.6. Summary

The `handleEqual` function is a safety mechanism to ensure that only valid mathematical expressions are processed, and any errors are gracefully handled by displaying "Error". It uses the `evaluate` function from the `math.js` library, which makes the evaluation safer compared to using `eval()`.

If you'd like to learn more about how `math.js` works and how to use it, you can refer to the official [Math.js documentation](https://mathjs.org/docs/).

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
<input type="button" value="=" className="equal" onClick={handleEqual} />
```

- Evaluates the mathematical expression in `value` using the JavaScript `eval()` function.
- Example: If `value` is `"3+5"`, clicking "=" sets `value` to `"8"`.

---

### 5. **Grouping Buttons**

Buttons are grouped using `<div>` elements to organize numbers and operators visually:

```jsx
<div>
  <input
    type="button"
    value="1"
    onClick={(e) => setValue(value + e.target.value)}
  />
  <input
    type="button"
    value="2"
    onClick={(e) => setValue(value + e.target.value)}
  />
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
