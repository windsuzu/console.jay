---
draft: false
date: 2024-05-27 16:59
tags:
  - react
  - server-action
---

`useFormStatus` can only be called in client components that are inside a `form` component. It shows the status information of the action which is called from that `form`.

```tsx
import { submitForm } from "./actions.js";

function Form({ action }) {
  return (
    <form action={action}>
      <Submit />
    </form>
  );
}
```

```tsx
"use client"
import { useFormStatus } from "react-dom";

function Submit() {
  const { pending } = useFormStatus();
  return (
    <button type="submit" disabled={pending}>
      {pending ? "Submitting..." : "Submit"}
    </button>
  );
}
```


> [!info] References
> -  [Data Fetching: Server Actions and Mutations | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)
> - [useFormStatus – React](https://react.dev/reference/react-dom/hooks/useFormStatus)
