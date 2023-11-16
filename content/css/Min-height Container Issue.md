---
draft: false
date: 2023-11-16 22:40
tags:
  - css
---
  
Using `min-height` instead of `height` to create a container element is a good approach. Because the height of a container is typically determined by its content and can vary with screen size, making use of `min-height` would be a safer option.

However, it won't work if you set an element's `height` using a percentage within a `min-height` container. As an example below, the `h1` element below will not adopt a height of `25vh` when its parent container has a `min-height` set to `50vh`.

```html
<div style="min-height: 50vh; background: #87cefa;">
  <h1 style="height: 50%; background: #eee8aa;">Test</h1>
</div>
```
![[min-height-container-issue.png]]

The issue occurs because a percentage height relies on a defined height. Since the parent's height is undefined, the `h1` cannot calculate its own height.

A temporary solution would be to manually calculate the height of `h1`, but this may cause other issues.
```html
<div style="min-height: 50vh; background: #87cefa;">
  <h1 style="height: 25vh; background: #eee8aa;">Test</h1>
</div>
```

A better approach is to refrain from defining the height of any children and use padding instead.


> [!info] References
> - [One of the most common CSS issues people run into - Kevin Powell](https://www.youtube.com/watch?v=6aHKdahOfCc)
