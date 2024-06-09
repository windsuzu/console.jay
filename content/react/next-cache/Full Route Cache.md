---
draft: false
date: 2024-06-09 17:29
tags:
  - react
  - nextjs
  - cache
---

![[full-route-cache.png]]
> Source: [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)

When Next.js builds our pages, it caches the ==generated HTML/RSCP in the full route cache== if the page **does not contain any dynamic data** (such as `dynamic URL parameters`, `cookies`, `headers`, `searchParams`, etc.). The full route cache is cleared each time it is redeployed.

>[!info]
>React Server Component Payload (RSCP) contains instructions for how client components should interact with rendered server components.

```tsx
import Link from "next/link"

async function getBlogList() {
  const blogPosts = await fetch("https://api.example.com/posts")
  return await blogPosts.json()
}

export default async function Page() {
  const blogData = await getBlogList()

  return (
    <div>
      <h1>Blog Posts</h1>
      <ul>
        {blogData.map(post => (
          <li key={post.slug}>
            <Link href={`/blog/${post.slug}`}>
              <a>{post.title}</a>
            </Link>
            <p>{post.excerpt}</p>
          </li>
        ))}
      </ul>
    </div>
  )
}
```

For example, the above `Page` is stored as HTML/RSCP in the full route cache at build time because it contains no dynamic data. The `fetch` request in `getBlogList` is cached in the [[data cache]], so it is considered static.

## Opting Out

1. If you opt out the [[data cache#Opting Out|data cache]], then the full route cache will also not be used.
2. If you use dynamic data in your page, the full route cache will not be used either. The dynamic data includes `headers`, `cookies`, `searchParams`, dynamic URL parameters like `id` in `/blog/[id]`.


> [!info] References
> - [Finally Master Next.js's Most Complex Feature - Caching (webdevsimplified.com)](https://blog.webdevsimplified.com/2024-01/next-js-app-router-cache/)
> - [Building Your Application: Caching | Next.js (nextjs.org)](https://nextjs.org/docs/app/building-your-application/caching#full-route-cache)
