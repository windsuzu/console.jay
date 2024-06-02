---
draft: false
date: 2024-06-02 17:53
tags:
  - react
  - nextjs
  - cache
---

Request memoization is more of a React feature rather than a Next.js feature. It caches `fetch` results that are made in server components **in a single render cycle**. It will return results from the cache if there are second and more `fetch` requests with same parameters (URL and options).

```tsx {8,17}
export default async function fetchUserData(userId) {
  // The `fetch` function is automatically cached by Next.js
  const res = await fetch(`https://api.example.com/users/${userId}`)
  return res.json();
}

export default async function Page({ params }) {
  const user = await fetchUserData(params.id)

  return <>
    <h1>{user.name}</h1>
    <UserDetails id={params.id} />
  </>
}

async function UserDetails({ id }) {
  const user = await fetchUserData(id)
  return <p>{user.name}</p>
}
```

For example, we have `Page` and `UserDetails` server components. When the `user` data is retrieved by the first `fetch` request in the `Page` component, the `user` data is also stored in the request memoization cache.

After that, the second `fetch` request in the `UserDetails` component will retrieve the stored data from the request memoization cache. The entire process happens in a single render cycle.

### Caching Non-`fetch` Requests

By default, React caches all `fetch` requests in request memoization. However, it also provides a `cache` function to wrap other non-`fetch` requests and make them behave like `fetch` requests.

```tsx
import { cache } from "react"
import { queryDatabase } from "./databaseClient"

export const fetchUserData = cache(userId => {
  // Direct database query
  return queryDatabase("SELECT * FROM users WHERE id = ?", [userId])
})
```

### Opting Out

If you don't want the request memoization to happen, you can pass a `signal` from the `AbortController` as a parameter to the `fetch` request. This prevents `fetch` result from being cached in the request memoization cache. However, it is not recommended to do this.

```tsx {2,4}
async function fetchUserData(userId) {
  const { signal } = new AbortController()
  const res = await fetch(`https://api.example.com/users/${userId}`, {
    signal,
  })
  return res.json()
}
```

> [!info] References
> - [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)
> - [Building Your Application: Caching | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/caching)
