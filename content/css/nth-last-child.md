---
draft: false
date: 2023-11-17 18:10
tags:
  - css
---

The `:nth-last-child` pseudo-class is used to select a group of elements by counting from the end among its sibling elements. It can also be utilized to implement a [[Quantity Query]], applying styles based on the item's number.

We are going to demonstrate how to use `:nth-last-child` with HTML code.

## 1. Select all even or odd elements counting from the end
Selecting elements whose position numbers are odd or even from the end can be easily achieved by using the keywords `odd` or `even`.
```html
<style>
	li:nth-last-child(odd) { ... }
</style>

<ul>
	<li>1</li>
	<li>2</li> selected
	<li>3</li>
	<li>4</li> selected
	<li>5</li>
	<li>6</li> selected (start from here)
</ul>
```

> [!tip]
> You can also use `2n+1` to represent `odd` and `2n` to represent `even`.

## 2. Select the specific element counting from the end
```css
<style>
	li:nth-last-child(3) { ... }
</style>

<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li> selected (count: 3)
	<li>5</li> (count: 2)
	<li>6</li> (count: 1)
</ul>
```

## 3. Select all elements
We can use `n` and `n+1` to select all elements, as the last element is labeled as 1, while `n` starts from 0.
```html
<style>
	li:nth-last-child(n+1) { ... }
</style>

<ul>
	<li>1</li> selected
	<li>2</li> selected
	<li>3</li> selected
	<li>4</li> selected
	<li>5</li> selected
	<li>6</li> selected (start from here)
</ul>
```

## 4. Select all elements before a specific position counting from the end
This notation can be represented as `n+b`. It will initially take `b` steps and then select all elements starting from the position it has landed.
```html
<style>
	li:nth-last-child(n+3) { ... }
</style>

<ul>
	<li>1</li> selected
	<li>2</li> selected
	<li>3</li> selected
	<li>4</li> selected (count: 3)
	<li>5</li> (count: 2)
	<li>6</li> (count: 1)
</ul>
```

## 5. Select elements by patterns counting from the end
This notation can be represented as `an+b`. It will initially take `b` steps and then select elements every `a` steps from the position it has landed.
```html
<style>
	li:nth-last-child(3n+2) { ... }
</style>

<ul>
	<li>1</li> 
	<li>2</li> selected
	<li>3</li> 
	<li>4</li> 
	<li>5</li> selected (count: 2)
	<li>6</li> (count: 1)
</ul>
```

## 6. Select the last b elements
By multiplying `n` by `-1`, it will select all elements in reverse order after `b` steps. Therefore, it appears as if selecting the last `b` elements.
```html
<style>
	li:nth-last-child(-n+3) { ... }
</style>

<ul>
	<li>1</li> 
	<li>2</li>
	<li>3</li> 
	<li>4</li> selected (count: 3)
	<li>5</li> selected (count: 2)
	<li>6</li> selected (count: 1)
</ul>
```



> [!info] References
> - https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-last-child
