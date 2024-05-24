---
draft: false
date: 2024-05-24 12:44
tags:
  - event
  - web-dev
---

Event delegation is a way to assign listeners to DOM elements. If you have a lot of similar child elements within a parent element. You can assign a listener to the parent and listen to all events from the children by checking `event.target` to minimize memory usage.

```html
<div id="container">
  <div class="tile"></div>
  <div class="tile"></div>
  <div class="tile"></div>
</div>;
```

```js
const container = document.querySelector("#container");
container.addEventListener(
  "click",
  (event) => (event.target.style.backgroundColor = bgChange())
);
```

See the real effect in [MDN's example](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#event_delegation:~:text=In%20the%20last%20section%2C%20we,the%20user%20clicks%20that%20tile.).

> [!info] References
> - [Introduction to events - Learn web development | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#event_delegation)
> - [請說明瀏覽器中的事件委派、捕獲、冒泡｜ExplainThis](https://www.explainthis.io/zh-hant/swe/fe-event-delegation-capture-bubble)
