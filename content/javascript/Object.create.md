---
draft: false
date: 2023-12-10 16:24
tags:
  - javascript
---

The `Object.create` method creates a new object that **inherits from the object passed as an argument**. If a property is missing in the new object, it will attempt to access the property from the prototype object. This delegation process allows you to share properties and methods among multiple objects.

```js
const parent = {
  name: 'Stacey',
  age: 35,
  heritage: 'Irish'
}

const child = Object.create(parent)
child.name = 'Ryan'
child.age = 7

console.log(child.name) // Ryan
console.log(child.age) // 7
console.log(child.heritage) // Irish
```

As the example above, the `child` object is created using the `Object.create` method and inherits properties from the `parent` object. When the `child.heritage` property is missing, it is looked up in the `parent` object and its value is inherited.

> [!info] References
> - [A Beginner's Guide to JavaScript's Prototype](https://ui.dev/beginners-guide-to-javascript-prototype)
