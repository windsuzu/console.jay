---
draft: false
date: 2024-06-01 18:00
tags:
  - react
  - server-action
---

`useActionState` is a hook to let you initialize a state for a function such as a [[server action]], and update that state based on the result of the action. 

`useActionState` is a great match with [[server action]] because it allows you to interact with `form` even before JavaScript has been executed on the client side.

One powerful use of `useActionState` is to handle errors that may be generated during validation in the [[server action]]. In the following example, we use `zod` to perform schema validation. If the parse fails, our `addProduct` action returns the errors as the new state of the first parameter destructuring from `useActionState`.

```tsx title="actions.ts"
const addSchema = z.object({
  name: z.string().min(1),
  description: z.string().min(1),
});

export const addProduct = async (prevState: unknown, formData: FormData) => {
  const result = addSchema.safeParse(Object.fromEntries(formData.entries()));
  
  if (!result.success) {
    return result.error.formErrors.fieldErrors;
  }
  
  // handle product adding
}
```

Even if we set the type of `prevState` to `unknown`, TypeScript is smart enough to know that the `type` of `error` is equal to `result.error.formErrors.fieldErrors`.

```tsx title="page.tsx"
export const ProductForm = ({ product }: { product: Product | null }) => {
  const [error, action] = useFormState(addProduct, {});

  return (
    <form action={action} className="space-y-8">
      <div className="space-y-2">
        <Label htmlFor="name">Name</Label>
        <Input
          type="text"
          id="name"
          name="name"
          required
          defaultValue={product?.name}
        />
        {error.name && <div className="text-destructive">{error.name}</div>}
      </div>
      
      {/* Other inputs...*/}
  </form>
  );
}
```


> [!info] References
> -  [Data Fetching: Server Actions and Mutations | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)
> - [useActionState – React](https://react.dev/reference/react/useActionState)
