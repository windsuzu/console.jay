---
draft: false
date: 2023-12-02 11:50
tags:
  - tbd
  - react
---

In React, a **controlled component** refers to a component whose behavior is entirely controlled or managed by React state. The component doesn't maintain its internal state; instead, it receives its current value and handles changes through props and callbacks provided by its parent or a higher-level component.

```tsx title="Example of a controlled component"
const [inputValue, setInputValue] = useState("");
const handleInputChange = (newValue: string) => {
    setInputValue(newValue);
  };
  
<input
  type="text"
  value={inputValue}
  onChange={(e) => handleInputChange(e.target.value)}
/>
```

## Controlled / Uncontrolled
The key distinction between controlled and uncontrolled components lies in how the state is managed: **controlled components** have their state managed externally, while **uncontrolled components** manage their own internal state. The table below compares the two in detail.

| **Aspect**             | **Controlled Components**                                                             | **Uncontrolled Components**                                                  |
| ---------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **State Management**   | Controlled externally by a parent component or higher-level component.                | Maintains internal state.                                                    |
| **Props for Value**    | Receives the current value via props (e.g., `value={...}`).                           | Manages its value internally.                                                |
| **Props for onChange** | Receives a callback function for handling changes via props (e.g., `onChange={...}`). | Handles changes internally, often using refs or other techniques.            |
| **Updates to State**   | State updates are communicated back to the parent component through callbacks.        | State changes may not be reflected immediately in the React component state. |
| **Predictability**     | More predictable behavior since the parent component is in control.                   | May have less predictable behavior due to internal state management.         |

## Imperative / Declarative Control
If you're already acquainted with [[Imperative and Declarative Programming]], there's just a slight difference between these two methods of controlling components. 

- In a imperative way, we will use a `ref` to control the component
- In a declarative way, we will 



> [!info] References
> - [Partially Controlled Components: A Declarative Design Pattern in React (jameskerr.blog)](https://www.jameskerr.blog/posts/partially-controlled-react-components/)
