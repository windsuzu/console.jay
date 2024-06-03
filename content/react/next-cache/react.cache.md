---
draft: false
date: 2024-06-03 15:55
tags:
  - react
  - nextjs
  - cache
---

By default, React caches all `fetch` requests in [[Request Memoization]]. However, it also provides a `cache` function to wrap other non-`fetch` requests and make them behave like `fetch` requests.

```tsx
import { cache } from "react"
import { queryDatabase } from "./databaseClient"

export const fetchUserData = cache(userId => {
  // Direct database query
  return queryDatabase("SELECT * FROM users WHERE id = ?", [userId])
})
```

> [!info] References
> - [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)
> - [cache – React](https://react.dev/reference/react/cache)
> - [Building Your Application: Caching | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/caching)
