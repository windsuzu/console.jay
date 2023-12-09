---
draft: false
date: 2023-12-05 17:40
tags:
  - javascript
---

**Functional instantiation** is a pattern that involves creating a function which accepts one or more arguments to instantiate an object. This function is consistently used to construct an object, hence it is referred to as a **"constructor function"**. 

**Functional instantiation** stems from the process of creating a simple object. While creating a single object is straightforward, it becomes inadequate when we need multiple objects that perform the same function.

```js title='creating a simple object'
let animal = {}
animal.name = 'Leo'
animal.energy = 10

animal.eat = function (amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}
```

To implement **functional instantiation**, we can simply incorporate the code used to create a basic object into a **constructor function**. In our example, this is the `Animal` function that accepts two arguments: `name` and `energy`.

```js title='functional instantiation'
function Animal (name, energy) {
  let animal = {}
  animal.name = name
  animal.energy = energy

  animal.eat = function (amount) {
    console.log(`${this.name} is eating.`)
    this.energy += amount
  }

  return animal
}

const leo = Animal('Leo', 7)
const snoop = Animal('Snoop', 10)
```

> [!tip]
> It is recommended to **capitalize the name of the constructor function**. This convention helps other developers recognize it as a constructor function.

## Shared Methods
You may observe that the `eat` function in our `Animal` constructor is repeatedly created for each object (`leo` and `snoop`) we instantiate. 

To address this issue and minimize memory usage, we could extract all functions from the constructor function and **place them in a separate object**. Then, when we instantiate an object from the constructor, we can **reference the function from the newly created object**.

```js
const animalMethods = {
  eat(amount) {
	console.log(`${this.name} is eating.`)
	this.energy += amount
  }
}

function Animal (name, energy) {
  let animal = {}
  animal.name = name
  animal.energy = energy
  animal.eat = animalMethods.eat

  return animal
}

const leo = Animal('Leo', 7)
const snoop = Animal('Snoop', 10)
```

> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
