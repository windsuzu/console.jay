---
draft: false
date: 2023-12-10 16:24
tags:
  - javascript
---

Prototypal instantiation utilizes [[Object.create]] and [[Prototype]] to create constructor functions used to generate object instances. It eliminates the need for [[Functional Instantiation#Shared Methods|creating shared methods in functional instantiation]].

```js
function Animal (name, energy) {
  let animal = Object.create(Animal.prototype)
  animal.name = name
  animal.energy = energy
  return animal
}

Animal.prototype.eat = function(amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

const leo = Animal('Leo', 7)

leo.eat(5); // Leo is eating.
console.log(leo.energy); // 12
```

> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
