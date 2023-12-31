---
draft: false
date: 2023-11-26 16:40
tags:
  - javascript
---

Pattern matching is a [[Imperative and Declarative Programming|declarative]] code-branching technique that manages multiple states without relying on [[Imperative and Declarative Programming|imperative constructs]] like `if`, `else`, or `switch`. While widely implemented in languages well-supported for [[functional programming]], such as Swift, Haskell, and Rust, it is still in the early stages of consideration for addition to EcmaScript (as of 2023). 

Fortunately, the library [ts-pattern](https://github.com/gvergnaud/ts-pattern) provides a means to implement pattern matching with features like **type-safety, exhaustiveness checking**, and more. 

In this note, we are going to demonstrate how you can integrate **pattern matching** into your standard state management code in React JSX components.

## 🔴 Ternaries

Let's examine how we typically implement a component with an API response. Ternaries are undoubtedly a default approach that a React developer would use when handling various statuses from an API response. 

However, there are two drawbacks to the approach of using ternaries:
1. It can be messy, especially when dealing with nested conditions.
2. It cannot accommodate all cases when new states or conditions are added.

```tsx
type State =
  | { status: "loading" }
  | { status: "error"; error: string }
  | { status: "success"; data: string };

const SomeComponent = ({ fetchState }: { fetchState: State }) => (
	<div>
		{fetchState.status === "loading" ? (
		  <p>Loading...</p>
		) : fetchState.status === "success" ? (
		  <p>{fetchState.data}</p>
		) : fetchState.status === "error" ? (
		  <p>Oops, an error occured: {fetchState.error}</p>
		) : null}
	</div>
);
```

## 🟠 Switch + IIFE +  Exhaustiveness Checking
We can use a `switch` statement to make the code look cleaner, but it will always require the use of an [IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE) (Immediately Invoked Function Expression) since a switch statement is not an expression that can be used directly in JSX in React.

Additionally, we can create a function named `safeGuard`, which takes an argument with the type `never`. This ensures that the argument passed to the default branch of the `switch` statement has been narrowed down to `never`, indicating that we have handled all possible `status` values from the API response.

```tsx {3,15,16}
// This function is just a way to tell TypeScript that this code
// should never be executed.
function safeGuard(arg: never) {}

const SomeComponent = ({ fetchState }: { fetchState: State }) => (
	<div>
	  {(() => {
	    switch (fetchState.status) {
	      case "loading":
	        return <p>Loading...</p>;
	      case "success":
	        return <p>{fetchState.data}</p>;
	      case "error":
	        return <p>Oops, an error occured: {fetchState.error}</p>;
	      default:
	        safeGuard(fetchState.status);
	    }
	  })()}
	</div>
);
```

## 🟢 ts-pattern
`ts-pattern` provides a `match` expression function to match all possibilities from the input without requiring an IIFE. It returns a [builder](https://en.wikipedia.org/wiki/Builder_pattern) for us to add our pattern matching cases.
- `.with()` takes two arguments. The first one is the **expected pattern** for this branch, and the second one is a **handler function with parameters narrowed down** to what matches the specified pattern.
- `.exhaustive()` is the final function in the builder that executes the `match` expression and returns the result from the matching branch. It also provides **exhaustiveness checking** to ensure that all cases from the input have been handled. 

> [!important] The exhaustiveness checking of `.exhaustive()`
> This checking occurs at compile time and comes with a **trade-off** in terms of performance, as the type checker needs to perform additional work.

```tsx
import { match } from 'ts-pattern';

const SomeComponent = ({ fetchState }: { fetchState: State }) => (
	<div>
	  {match(fetchState)
	    .with({ status: "loading" }, ({ status }) => <p>{status}...</p>)
	    .with({ status: "success" }, ({ data }) => <p>{data}</p>)
	    .with({ status: "error" }, ({ error }) => <p>Error: {error}</p>)
	    .exhaustive()}
	</div>;
);
```

> [!seealso] An alternative to `.exhaustive()`
> You can use `.otherwise()` instead to execute the expression without **exhaustiveness checking**. It takes a handler function to return if none of the cases are matched.
> ```tsx
>  .otherwise(() => fetchState);
> ```

You can explore more details about `ts-pattern` [in the documentation](https://github.com/gvergnaud/ts-pattern#documentation), including information on different data structures for pattern matching, advanced methods for pattern matching with `.with()`, type inference, and more.

> [!info] References
> - [Unraveling the magic of Pattern Matching (swan.io)](https://www.swan.io/blog-posts/unraveling-the-magic-of-pattern-matching)
> - [gvergnaud/ts-pattern: 🎨 The exhaustive Pattern Matching library for TypeScript, with smart type inference.](https://github.com/gvergnaud/ts-pattern)
> - [Bringing Pattern Matching to TypeScript 🎨 Introducing TS-Pattern - DEV Community](https://dev.to/gvergnaud/bringing-pattern-matching-to-typescript-introducing-ts-pattern-v3-0-o1k) 

