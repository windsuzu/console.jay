---
draft: false
date: 2023-12-19 16:28
tags:
  - javascript
---

If a method is closely associated with a constructor or class but should not be used on individual instances, where is the appropriate location for this method? For example, consider an `Animal` constructor with common utility methods stored in its prototype. In this case, a function that finds the animal with the most energy from an array of animals would be more appropriately placed as a static method on the `Animal` class.

```js title="Static Method with Prototypal Instantiation" {11-17}
function Animal(name, energy) {
  this.name = name
  this.energy = energy
}

Animal.prototype.eat = function(amount) {
  console.log(`${this.name} is eating.`)
  this.energy += amount
}

// Create a static method in the Animal constructor
Animal.mostEnergetic = function(animals) {
  const sortedByMostEnergy = animals.sort((a,b) => {
    return b.energy - a.energy
  })
  return sortedByMostEnergy[0].name
}

const leo = new Animal('Leo', 7)
const snoop = new Animal('Snoop', 10)

// Use the static method directly from the constructor
console.log(Animal.mostEnergetic([leo, snoop])) // Snoop
```

When dealing with a method specific to a `class`, not meant for individual instance use, declare it as a static method of the class.

```js title="Static method with ES6 Classes" {11-17}
class Animal {
  constructor(name, energy) {
    this.name = name
    this.energy = energy
  }
  eat(amount) {
    console.log(`${this.name} is eating.`)
    this.energy += amount
  }
  
  // Create a static method in the Animal class
  static mostEnergetic(animals) {
    const sortedByMostEnergy = animals.sort((a,b) => {
	  return b.energy - a.energy
	})
	return sortedByMostEnergy[0].name
  }
}

const leo = new Animal('Leo', 7)
const snoop = new Animal('Snoop', 10)

// Use the static method directly from the class
console.log(Animal.mostEnergetic([leo, snoop])) // Snoop
```

> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
