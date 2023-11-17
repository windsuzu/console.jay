---
draft: false
date: 2023-11-17 18:45
tags:
  - css
  - tbd
---

The **quantity query** is a technique that utilizes `nth-last-child` and [subsequent-sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Subsequent-sibling_combinator) (the tilde symbol `~`) to apply styles to a group of elements when the number of elements in the group exceeds a certain threshold. 

```html
<style>
	/* If there are at least 4 items, style them all */
	li:nth-last-child(n + 4),
	li:nth-last-child(4) ~ li { ... }
</style>

All the li elements below will not be selected.
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ul>

All the li elements below will be selected.
<ul>
	<li>1</li> (selected from n + 4)
	<li>2</li> (selected from n + 4)
	<li>3</li> (selected from 4 ~ li)
	<li>4</li> (selected from 4 ~ li)
	<li>5</li> (selected from 4 ~ li)
</ul>
```



> [!info] References
> - [:nth-last-child() - CSS: Cascading Style Sheets | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-last-child#quantity_query)
> - https://ishadeed.com/article/conditional-css-has-nth-last-child
