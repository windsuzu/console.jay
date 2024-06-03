---
draft: false
date: 2024-06-03 16:39
tags:
  - react
  - nextjs
  - cache
---

![[data-cache.png]]
> Source: [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)

By default, Next.js automatically caches data in the data cache for every `fetch` request in server components. ==The data cache is the last cache Next.js hits== before fetching data from APIs or the database. It is also ==persistent across multiple requests and users==. 

If there are 100 users requesting the same data, Next.js will fetch it only once, store it in the data cache, and return it from the cache to 100 users. 

```tsx {3}
export default async function Page({ params }) {
  const city = params.city
  const res = await fetch(`https://api.globetrotter.com/guides/${city}`)
  const guideData = await res.json()

  return (
    <div>
      <h1>{guideData.title}</h1>
      <p>{guideData.content}</p>
      {/* Render the guide data */}
    </div>
  )
}
```

For example, the `guideData` will only be fetched from the API once and stored in the data cache. All users will get the data from the data cache instead of fetching it from the API.
## Revalidation

==Data cache is never cleared, even if you redeploy your application.== The only way to update the cache is to explicitly tell Next.js to do so using **time-based revalidation** or **on-demand revalidation.**

### Time-based revalidation

We can tell Next.js to automatically revalidate the data in the data cache by declaring a time period. You can either declare the time as the second parameter (options) in the `fetch` function, or declare it as a config option of the page.

Next.js implements time-based revalidation with a pattern called `stale-while-revalidate`. Here is how it works: 

1. `fetch` the data from the API and store it in the data cache.
2. Within 1 hour, each `fetch` returns only the data from the data cache.
3. After 1 hour, the first `fetch` returns the data from the data cache, but it also makes the request with API and updates the data cache with new data.
4. The next `fetch` returns the new data in the data cache.

```tsx title="Revalidate a fetch request"
// The cache of this fetch will be revalidated after 1 hour
const res = fetch(`https://api.globetrotter.com/guides/${city}`, {
  next: { revalidate: 3600 },
})
```

```tsx title="Revalidate whole page"
// all cache of this page will be revalidated after 1 hour
export const revalidate = 3600

export default async function Page({ params }) {
  const city = params.city
  const res = await fetch(`https://api.globetrotter.com/guides/${city}`)
  const guideData = await res.json()

  return (
    <div>
      <h1>{guideData.title}</h1>
      <p>{guideData.content}</p>
      {/* Render the guide data */}
    </div>
  )
}
```

> [!important] 
> The time period declared in the fetch function has higher priority than the one declared in the page when two methods are used at the same time.

### On-demand Revalidation

There are two ways to revalidate the data cache by calling functions instead of waiting for a period of time.

- `revalidatePath` will clear the cache of all `fetch` requests on the path you pass.

```tsx {6}
import { revalidatePath } from "next/cache"

export async function publishArticle({ city }) {
  createArticle(city)

  revalidatePath(`/guides/${city}`)
}
```

- `revalidateTag` will clear the cache of all `fetch` requests that have `tags` specified in their `fetch` function.

```tsx
const res = fetch(`https://api.globetrotter.com/guides/${city}`, {
  next: { tags: ["city-guides"] },
})
```

```tsx {6}
import { revalidateTag } from "next/cache"

export async function publishArticle({ city }) {
  createArticle(city)

  revalidateTag("city-guides")
}
```
## Opting Out

If you don't want Next.js to cache `fetch` requests in the data cache, for example, if the `fetch` results need to be fresh for every user, you can declare `no-store` in your `fetch` function to disable the data cache.

```tsx
const res = fetch(`https://api.globetrotter.com/guides/${city}`, {
  cache: "no-store",
})
```

Another way is to declare `force-dynamic` to the `dynamic` segment config option of the page, or set `0` to `revalidate`. Both declarations will disable the data cache for all `fetch` requests on the same page.

```tsx
export const dynamic = "force-dynamic"
```

```tsx
export const revalidate = 0
```

## Caching Non-`fetch` Requests

You can use the experimental [[next.cache.unstable_cache|unstable_cache]] API of Next.js to cache non-`fetch` requests in the data cache.


> [!info] References
> - [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)
> - [Building Your Application: Caching | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/caching)
