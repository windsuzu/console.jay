---
draft: false
date: 2023-12-31 21:57
tags:
  - javascript
---

In JavaScript, while the `for...in` loop is often used to iterate over an object's properties, it's important to note that it includes those inherited from its prototype chain. For example, 

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
