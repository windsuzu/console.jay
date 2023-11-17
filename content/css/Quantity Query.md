---
draft: false
date: 2023-11-17 22:13
tags:
  - css
---

The **quantity query** is a technique that utilizes the combination of [[nth-last-child]] and the [subsequent-sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Subsequent-sibling_combinator) (the tilde symbol `~`) to apply styles to a group of elements when the number of elements in the group exceeds a certain threshold.

```html
<style>
	/* If there are at least 4 items, style them all */
	li:nth-last-child(n + 4),
	li:nth-last-child(4) ~ li { ... }
</style>

(1) All the li elements below will not be selected.
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ul>

(2) All the li elements below will be selected.
<ul>
	<li>1</li> (selected from n + 4)
	<li>2</li> (selected from n + 4)
	<li>3</li> (selected from 4 ~ li)
	<li>4</li> (selected from 4 ~ li)
	<li>5</li> (selected from 4 ~ li)
</ul>
```

## Quantity Query and `:has` Selector
The **quantity query** can be incredibly powerful when used in conjunction with the `:has` selector! The article [Conditional CSS with :has and :nth-last-child written by Ahmad](https://ishadeed.com/article/conditional-css-has-nth-last-child) demonstrates 7 use cases of the **quantity query** combined with the `:has` selector. I chose one to showcase its power!

```html
<div class="modal">
	<h1>Title</h1>
	<p>...</p>
	
	<div class="actions">
		<button class="cancel">Cancel</button>
		<button class="ok">OK, I understand</button>
	</div>
</div>
```

When creating a modal or dialog, it's common to include one or multiple buttons at the bottom. By default, we can position the button in the center. Additionally, we can use a **quantity query and the :has selector** to place the buttons at the end of the block when there are two or more buttons.

```css
.actions {
	display: flex;
	/* Center the button by default */
	justify-content: center;
	gap: 1rem;
}

/* If there are 2 buttons or more */
.actions:has(button:nth-last-child(n + 2)) {
	justify-content: flex-end;
}
```

When there are two or more buttons, the `<div class="actions">` will position the buttons to the rightmost by changing the `justify-content` to `flex-end`.
![[Pasted image 20231117220117.png]]

When there is only one button, the `:has` selector and quantity query will not trigger, so the button will be placed in the center by default.
![[Pasted image 20231117220134.png]]

> [!info] References
> - [:nth-last-child() - CSS: Cascading Style Sheets | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-last-child#quantity_query)
> - https://ishadeed.com/article/conditional-css-has-nth-last-child
