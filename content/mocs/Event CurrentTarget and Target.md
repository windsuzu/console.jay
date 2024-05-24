---
draft: false
date: 2024-05-24 15:52
tags:
  - web-dev
  - browser-event
---

The easiest way to distinguish between `currentTarget` and `target` is to figure out which one the listener is listening to. `currentTarget` is the one that listener is listening to, while `target` is the one we are interacting with on the screen.

- **`currentTarget`**: This refers to the element to which the event listener is attached.
- **`target`**: This refers to the element that triggered the event.

```html
<form>
  <div>
    <p>Hey</p>
  </div>
</form>
```

```js
const form = document.querySelector("form");

form.addEventListener("click", (event) => {
  console.log("CurrentTarget: ", event.currentTarget);
  console.log("Target: ", event.target);
});

// CurrentTarget: <form>
// Target: <p>
```

> [!info] References
> - [請說明瀏覽器中的事件委派、捕獲、冒泡｜ExplainThis](https://www.explainthis.io/zh-hant/swe/fe-event-delegation-capture-bubble)
