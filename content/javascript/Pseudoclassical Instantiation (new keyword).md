---
draft: false
date: 2023-12-18 15:41
tags:
  - javascript
---

This note assumes familiarity with the following concepts:
1. Sharing methods between object instances using the [[Prototype]] property.
2. Creating objects that inherit properties from another object using [[Object.create]] when property access fails.
3. Building constructor functions using [[Prototypal instantiation]].

```js
function Animal(name, energy) {
  let animal = Object.create(Animal.prototype)
  animal.name = name
  animal.energy = energy
  return animal
}

Animal.prototype.eat = function(amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

const leo = Animal("Leo", 10)
```

**Pseudoclassical instantiation** is a syntactic shortcut in JavaScript that leverages the `new` keyword to implicitly perform `Object.create` and return a new object whose prototype is set to the constructor's prototype. This approach mimics classical object-oriented inheritance patterns while utilizing JavaScript's prototypal underlying mechanism.

```js
function Animal(name, energy) {
  // let this = Object.create(Animal.prototype)
  
  this.name = name
  this.energy = energy
  
  //return animal
}

Animal.prototype.eat = function (amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

const leo = new Animal("Leo", 10)
```

**Omitting the `new` keyword when instantiating an object with pseudoclassical instantiation results in neither the `this` object being allocated nor the implicit return triggered.** This is because the `new` keyword is crucial for invoking the constructor function with the proper context and memory allocation.

```js
function Animal(name, energy) {
  this.name = name
  this.energy = energy
}

const leo = Animal('Leo', 7)
console.log(leo) // undefined
```


> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
