---
draft: false
date: 2023-12-19 15:17
tags:
  - javascript
---

Before ES6, JavaScript used functions and the [[Prototype]] property to share methods across instances, which is known as [[Pseudoclassical Instantiation (new keyword)]]. This approach required understanding the nuances of JavaScript’s prototype chain and [[Functional Instantiation|constructor functions]]. Here's an example of a pseudoclassical constructor:

```js
function Animal(name, energy) {
  this.name = name
  this.energy = energy
}

Animal.prototype.eat = function(amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

const leo = new Animal('Leo', 7)
```

The `class` keyword introduced in ES6 is syntactical sugar over the Pseudoclassical pattern. It offers a cleaner and more intuitive way to define a class’s constructor and its prototype methods. It aligns with the class-based inheritance found in other languages, making JavaScript more accessible to a broader range of developers and improving code readability and maintainability.

```js
class Animal {
  constructor(name, energy) {
    this.name = name
    this.energy = energy
  }
  
  eat(amount) {
    console.log(`${this.name} is eating.`)
    this.energy += amount
  }
}

const leo = new Animal('Leo', 7)
```

The introduction of the `class` syntax is part of JavaScript’s evolution to improve developer experience without changing the fundamental prototype-based nature of the language.

> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
