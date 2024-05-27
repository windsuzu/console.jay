---
draft: false
date: 2024-05-24 15:45
tags:
  - web-dev
  - browser-event
---

When you click on a DOM element with an event listener, the browser first performs top-down event capture, and then, when it has captured the final target, it starts bubbling bottom-up.

![[event-capturing-and-bubbling.png]]
> Source: [Event Bubbling and Capturing in JavaScript - javatpoint](https://www.javatpoint.com/event-bubbling-and-capturing-in-javascript)

However, event capturing is set to false by default, which means that event listeners would only return a callback during the bubbling phase. Unless you set the third parameter of `addEventListener` to `true`.

```js {3}
element.addEventListener('click', function(event) {
    console.log('Event handler executed during capturing phase');
}, true);
```

If you want to stop bubbling at the child element, you can use `event.stopPropagation()` in the listener that listens to that child.

```js
document.getElementById('child').addEventListener('click', function(event) {
    // Perform some action for the child element
    console.log('Child element clicked');
    
    // Stop the event from bubbling up to parent elements
    event.stopPropagation();
});

document.getElementById('parent').addEventListener('click', function(event) {
    // This will not be executed if the event.stopPropagation() is called
    console.log('Parent element clicked');
});
```


> [!info] References
> - [Introduction to events - Learn web development | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)
> - [請說明瀏覽器中的事件委派、捕獲、冒泡｜ExplainThis](https://www.explainthis.io/zh-hant/swe/fe-event-delegation-capture-bubble)
> - [[DOM] Event Propagation I : 事件捕捉和冒泡-Event Capture & Bubble | by Huge Gun | Medium](https://hsien-w-wei.medium.com/dom-event-propagation-i-%E4%BA%8B%E4%BB%B6%E6%8D%95%E6%8D%89%E5%92%8C%E5%86%92%E6%B3%A1-event-capture-bubble-8214bf146b35)
> - [Event Bubbling and Capturing in JavaScript - javatpoint](https://www.javatpoint.com/event-bubbling-and-capturing-in-javascript)
