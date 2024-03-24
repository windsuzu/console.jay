---
draft: false
date: 2024-01-01 01:19
tags:
  - javascript
---

While the `for...in` loop in JavaScript offers a convenient way to iterate over an object's properties, it's crucial to remember that it encompasses properties inherited from the prototype chain. This means you'll also encounter properties defined in parent objects or prototypes. Here's an example:

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

**To specifically target properties directly owned by the `Animal` instance, we leverage the `hasOwnProperty()` method.** This method determines whether a property is directly defined on the object itself, as opposed to being inherited through the prototype chain.

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
