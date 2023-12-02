---
draft: false
date: 2023-12-02 17:29
tags:
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

In an imperative approach, we utilize a `ref` to control the component, while in a declarative approach, we pass `props` for control. React also promotes the declarative style of programming.

### Example of imperative control

```tsx title='Imperative control using refs'
const ImperativeComponent = () => {
  const inputRef = useRef(null);

  const handleButtonClick = () => {
    // Imperative DOM manipulation
    inputRef.current.focus();
  };

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleButtonClick}>Focus Input</button>
    </div>
  );
};
```

### Example of declarative control
```tsx title="Declarative control using props"
const DeclarativeComponent = () => {
  const [inputValue, setInputValue] = useState("");

  const handleInputChange = (e) => {
    // Declarative state update
    setInputValue(e.target.value);
  };

  return (
    <input type="text" value={inputValue} onChange={handleInputChange} />
  );
};
```

## Partially Controlled Components
In this article, [Partially Controlled Components: A Declarative Design Pattern in React](https://www.jameskerr.blog/posts/partially-controlled-react-components/), James Kerr introduces a novel approach to creating components, allowing consumers to progressively implement the component from an uncontrolled to a controlled fashion. This approach draws inspiration from the API of the `React Input Element`.

```tsx
// uncontrolled
<input />

// uncontrolled with an initial value
<input initialValue="Default" />

// controlled
<input value={value} onChange={(e) => setValue(e.target.value)} />
```


> [!info] References
> - [Partially Controlled Components: A Declarative Design Pattern in React (jameskerr.blog)](https://www.jameskerr.blog/posts/partially-controlled-react-components/)
