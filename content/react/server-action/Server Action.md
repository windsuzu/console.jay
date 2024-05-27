---
draft: false
date: 2024-05-27 18:23
tags:
  - react
  - server-action
---

Server actions are asynchronous functions that only run as a `POST` request on the server and can be invoked in both client and server components.

You can create server actions in a single file or another function, and in both cases, they should be defined with a `"use server"` directive.

```tsx title="Creating server actions in a file"
// src/app/_actions/posts.ts

'use server'
 
import { redirect } from 'next/navigation'
import { revalidateTag } from 'next/cache'
 
export async function createPost(id: string) {
  try {
    // ...
  } catch (error) {
    // ...
  }
 
  revalidateTag('posts') // Update cached posts
  redirect(`/post/${id}`) // Navigate to the new post page
}
```

```tsx title="Creating server actions in a function"
// src/app/page.tsx

export default function Page() {
  async function createInvoice(formData: FormData) {
    'use server'
    try {
	    // ...
    } catch (error) {
	    // ...
    }

    revalidatePath('/') // revalidate cache
  }
 
  return <form action={createInvoice}>...</form>
}
```

You can use the `bind` method if you want to pass additional arguments to server actions instead of just `FormData`.

```tsx {6}
'use client'
 
import { updateUser } from './actions'
 
export function UserProfile({ userId }: { userId: string }) {
  const updateUserWithId = updateUser.bind(null, userId)
 
  return (
    <form action={updateUserWithId}>
      <input type="text" name="name" />
      <button type="submit">Update User Name</button>
    </form>
  )
}
```

```ts
'use server'
 
export async function updateUser(userId, formData) {}
```

There are two useful hooks you can use with server action, you can view their details and usage from their own pages.

1. [[useFormStatus]]: Retrieving status information of current submitting form.
2. [[useActionState (useFormState)]]: Retrieving action return object as a state.

You can even invoke server actions from event handlers (e.g., `onClick`, `onChange`) and `useEffect`. See [Data Fetching: Server Actions and Mutations | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations#non-form-elements) for implementation details.

```tsx
'use client'
 
import { incrementLike } from './actions'
import { useState } from 'react'
 
export default function LikeButton({ initialLikes }: { initialLikes: number }) {
  const [likes, setLikes] = useState(initialLikes)
 
  return (
    <>
      <p>Total Likes: {likes}</p>
      <button
        onClick={async () => {
          const updatedLikes = await incrementLike()
          setLikes(updatedLikes)
        }}
      >
        Like
      </button>
    </>
  )
}
```

```tsx
'use client'
 
import { publishPost, saveDraft } from './actions'
 
export default function EditPost() {
  return (
    <form action={publishPost}>
      <textarea
        name="content"
        onChange={async (e) => {
          await saveDraft(e.target.value)
        }}
      />
      <button type="submit">Publish</button>
    </form>
  )
}
```

```tsx
'use client'
 
import { incrementViews } from './actions'
import { useState, useEffect } from 'react'
 
export default function ViewCount({ initialViews }: { initialViews: number }) {
  const [views, setViews] = useState(initialViews)
 
  useEffect(() => {
    const updateViews = async () => {
      const updatedViews = await incrementViews()
      setViews(updatedViews)
    }
 
    updateViews()
  }, [])
 
  return <p>Total Views: {views}</p>
}
```


> [!info] References
> - [Data Fetching: Server Actions and Mutations | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)
