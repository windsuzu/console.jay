---
draft: false
date: 2023-11-25 22:52
tags:
  - javascript
---

Imparative and declarative programming represent two distinct approaches to completing a function. These programming paradigms are ubiquitous in various languages, and in this note, I will illustrate the contrast between them using JavaScript and DOM manipulation.

## Imperative Programming

### HOW
In imperative programming, we articulate a step-by-step process to accomplish a task.

### WHAT
We explicitly list each instruction, specifying the precise sequence of actions to be performed.

### Example (JavaScript DOM)
```js
var paragraph = document.createElement('p');
paragraph.textContent = 'Hello, World!';
document.body.appendChild(paragraph);
```

### Example (JavaScript Function)
```js
function sumArray(arr) {
  let sum = 0;
  for (let i = 0; i < arr.length; i++) {
    sum += arr[i];
  }
  return sum;
}

const numbers = [1, 2, 3, 4, 5];
const result = sumArray(numbers);
console.log(result); // Output: 15
```

### More
Imperative programming often involves explicit control flow using constructs like loops and conditionals. In Imperative code, side effects are common, with functions modifying external state or having observable interactions with the outside world.

## Declarative Programming

### HOW
Declarative programming centers on describing the final result or outcome without specifying the process to achieve it.

### WHAT
You declare what you want, leaving the underlying system to handle the execution. For instance, when using the React JSX function to render the UI, you don't need to delve into the details of the virtual DOM. Similarly, when employing `reduce` to sum an array, you can achieve the desired result without needing to understand the internal workings of the underlying system.

### Example (React JSX)
```jsx
function App() {
  return (
    <div>
      <p>Hello, World!</p>
    </div>
  );
}
```

### Example (Higher-Order Function)
```js
const numbers = [1, 2, 3, 4, 5];
const result = numbers.reduce((sum, num) => sum + num, 0);
console.log(result); // Output: 15
```

### More
[[Functional programming]] is a type of declarative programming that emphasizes using functions to express computations and discourages changing the state or mutating data.