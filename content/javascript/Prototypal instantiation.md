---
draft: false
date: 2023-12-10 11:36
tags:
  - javascript
---

Prototypal instantiation utilizes the [[Prototype]] to create constructor functions used to generate object instances. It eliminates the need for [[Functional Instantiation#Shared Methods|creating shared methods in functional instantiation]].

```js
function Animal (name, energy) {
  let animal = {}
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
> - 
