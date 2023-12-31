---
draft: false
date: 2023-12-31 20:20
tags:
  - javascript
---

To retrieve all properties of an object, including those inherited from its prototype, employ a `for...in` loop.

```js
function Animal (name, energy) {
  this.name = name
  this.energy = energy
}

Animal.prototype.eat = function (amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

const leo = new Animal('Leo', 7)

for (let key in leo) {
  console.log(`Key: ${key}. Value: ${leo[key]}`)
}

// Key: name. Value: Leo
// Key: energy. Value: 7

// Key: eat. Value: function (amount) {
//  console.log(`${this.name} is eating.`)
//  this.energy += amount
//}
```



```js
for (let key in leo) {
  if (leo.hasOwnProperty(key)) {
    console.log(`Key: ${key}. Value: ${leo[key]}`)
  }
}

// Key: name. Value: Leo
// Key: energy. Value: 7
```



> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype) 
