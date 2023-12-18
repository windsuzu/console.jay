---
draft: false
date: 2023-12-18 13:18
tags:
  - javascript
---

Every function in JavaScript has a property called `prototype` that references an object. This object acts as a shared prototype for all instances created with the function as a constructor. Since the prototype object is shared, any changes made to it will be reflected in all instances.

> [!note]
> The prototype chain is a fundamental concept in JavaScript inheritance.
  
The code below demonstrates how to create instances by calling a constructor function with [[Pseudoclassical Instantiation (new keyword)]] and shares a prototype that can be modified in the constructor.

```js
// Creating a constructor function
function Person(name) {
  this.name = name;
}

// Adding a method to the prototype before initializing any instances
Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

// Creating instances and accessing prototype properties and methods
const person1 = new Person('John');
const person2 = new Person('Jane');

person1.greet(); // Output: Hello, my name is John
person2.greet(); // Output: Hello, my name is Jane
```

The prototype can be modified even after instances are already initialized. Any changes made to the prototype will be reflected in all existing instances.

```js
// Adding another method to the prototype
Person.prototype.shock = function() {
  console.log(this.name + " says: Oh my god!");
}

person1.shock(); // Output: John says: Oh my god!
person2.shock(); // Output: Jane says: Oh my god!
```

> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
