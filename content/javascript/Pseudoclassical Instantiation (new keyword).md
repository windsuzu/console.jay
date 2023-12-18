---
draft: false
date: 2023-12-18 13:32
tags:
  - tbd
  - javascript
---

This note assumes you already understand the following concepts:
1. Use [[Prototype]] to share methods between instances
2. Use [[Object.create]] to create an object that looks up the inherited object's properties when invoke failed 
3. Use [[Prototypal instantiation]] to build a constructor function

```js
function Animal (name, energy) {
  let animal = Object.create(Animal.prototype)
  animal.name = name
  animal.energy = energy
  return animal
}
const leo = Animal("Leo", 10)
```

**Pseudoclassical Instantiation** is a syntax sugar in JavaScript that utilize the `new` keyword to perform the `Object.create` and `return` parts under the hood when we build a constructor function.

```js
function Animal (name, energy) {
  // let this = Object.create(Animal.prototype)
  this.name = name
  this.energy = energy
  //return animal
}
const leo = new Animal("Leo", 10)
```






> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
