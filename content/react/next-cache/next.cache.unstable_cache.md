---
draft: false
date: 2024-06-03 16:57
tags:
  - react
  - nextjs
  - cache
---

Next.js provides an experimental API called `unstable_cache`. It caches non-`fetch` requests in the [[data cache]], which can be shared between users. It takes 3 parameters:

1. The function you want to cache.
2. The key for the cache.
3. (Optional) Options for revalidation time or tags.

```tsx {4}
import { getGuides } from "./data"
import { cache as unstable_cache } from "next/cache"

const getCachedGuides = cache(city => getGuides(city), ["guides-cache-key"])

export default async function Page({ params }) {
  const guides = await getCachedGuides(params.city)
  // ...
}
```

In the example, we cache the `getGuides` function in the [[data cache]] with the key `["guides-cache-key"]`. The second time you call `getCachedGuides`, it will retrieve data from the [[data cache]] instead of calling `getGuides`.

> [!info] References
> - [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)
> - [Building Your Application: Caching | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/caching)
> - [Functions: unstable_cache | Next.js (nextjs.org)](https://nextjs.org/docs/app/api-reference/functions/unstable_cache)
