---
draft: false
date: 2023-12-10 11:11
tags:
  - javascript
---

Every function in JavaScript has a property called `prototype` that references an object. This object acts as a shared prototype for all instances created with the function as a constructor. Since the prototype object is shared, any changes made to it will be reflected in all instances.

> [!note]
> The prototype chain is a fundamental concept in JavaScript inheritance.
  
The code below demonstrates how to create instances by calling a constructor function and shares a prototype that can be modified in the constructor.

```js
// Creating a constructor function
function Person(name) {
  this.name = name;
}

// Adding a method to the prototype before any instances are initailized.
Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person('John');
const person2 = new Person('Jane');

person1.greet(); // Output: Hello, my name is John
person2.greet(); // Output: Hello, my name is Jane

console.log(person1.name); // Output: John
console.log(person2.name); // Output: Jane
```




> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
