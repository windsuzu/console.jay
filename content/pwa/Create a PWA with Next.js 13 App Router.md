---
title: Create a PWA with Next.js 13 App Router
draft: false
date: 2023-09-18 10:55
tags:
  - pwa
  - learning
---

> [!tldr] TL;DR
> Creating PWAs with Next.js 13 and the App Router is a valuable skill. Most tutorials are outdated, and `next-pwa` isn't actively maintained. Instead, I recommend using `@ducanh2912/next-pwa`. Here are the steps:
> 1. Install `@ducanh2912/next-pwa` and `webpack`.
> 2. Wrap Next.js config with `withPWA` plugin
> 3. Generate icons with `pwa-asset-generator`
> 4. Add `manifest.json` and metadata to `app/layout.tsx`
> 5. Exclude certain PWA files from your repo with `.gitignore.`

After learning about [[PWA (Progressive Web Apps)]] and [[Create a PWA]], I believe it's a valuable skill to explore creating a PWA with Next.js 13 and the app router. However, the article is limited (Most online tutorials are outdated if you want to use the app router feature^[[How to Create a PWA With Next.js in 10 Minutes - YouTube](https://www.youtube.com/watch?v=ARNN_zmrwcw)], and it appears that the well-known library `next-pwa` is no longer actively maintained.

The problems you might encounter when implementing a PWA using outdated tutorials often revolve around service worker compatibility or requirements such as `pages` folder, as mentioned in [this Reddit post](https://www.reddit.com/r/nextjs/comments/16guio3/does_anyone_know_of_a_good_guide_to_setting_up_a/). However, comments in this post also suggest trying [`@ducanh2912/next-pwa`](https://github.com/DuCanhGH/next-pwa), a forked version of `next-pwa` that is compatible with App Router.

---

Here, I'd like to share the steps to successfully convert a project into a PWA using Next.js 13's App Router. Because `@ducanh2912/next-pwa` offers [excellent documentation](https://ducanh-next-pwa.vercel.app/docs/next-pwa/getting-started) on how to convert an existing project into a PWA. You can simply follow the installation and usage instructions from the documentation. Additionally, I will share how I made it work and what to pay attention to in each step.

## Steps 1. Install `@ducanh2912/next-pwa`
Remember to install `@ducanh2912/next-pwa` in your project's dependencies and `webpack` in devDependencies using your package manager.
```bash
yarn add @ducanh2912/next-pwa && yarn add -D webpack
```

---
## Step 2. Wrap the Next config  with the configured `withPWA` plugin
Because my project is using ESM as its module system, I will show you how to wrap the Next.js config with `withPWA` in ESM.
```js title="next.config.js"
import NextPWA from "@ducanh2912/next-pwa";

const withPWA = NextPWA({
  // output directory for service worker
  dest: "public",
  // Whether `next-pwa` should be disabled.
  disable: process.env.NODE_ENV === "development",
  // automatically register the service worker for you
  register: true,
});

/**
 * @type {import('next').NextConfig}
 **/
const moduleExports = { ... }
					   
export default withPWA(moduleExports);
```

---
## Step 3. Generate icons using **[pwa-asset-generator](https://github.com/elegantapp/pwa-asset-generator)**
I generate a `manifest.json` file in the `public` folder using [PWA Manifest Generator | SimiCart](https://www.simicart.com/manifest-generator.html/) (skipping the icons part). Then, I also create a temporary `index.html` file in the `public` folder for `pwa-asset-generator` to populate with metadata, which can be later added to `layout.tsx` as mentioned in step 4.

```bash title="Run this in the root of your project"
npx pwa-asset-generator 
  # input icon
  ./public/logo.svg
  # output icons directory
  ./public/pwa-assets
  # automatically fill splash screen and icon meta tags to index.html
  --index ./public/index.html
  # automatically update manifest file with the generated icons
  --manifest ./public/manifest.json
  # also generate favicon image and its meta tag
  --favicon true
  # increate the image quality to 80
  --quality 80
  # make the icon transparent
  --opaque false
```

---
## Step 4. Add `manifest.json` and metadata to `app/layout.tsx`
After preparing the `manifest.json` and your icons, you can now add the required metadata to `app/layout.tsx`. There are a few things to note. Firstly, you can add `favicon` and `apple-icons` as described in the Next.js official documentation under [generateMetadata - icons](https://nextjs.org/docs/app/api-reference/functions/generate-metadata#icons). Secondly, ensure that `manifest.json` is linked to your app using `manifest` property.
```tsx title="app/layout.tsx" {12-13,15,21}
const APP_NAME = "MyPWA";
const APP_TITLE_TEMPLATE = "%s - MyPWA";
const APP_DESCRIPTION = "My awesome PWA.";

export const metadata: Metadata = {
    title: APP_NAME,
    description: APP_DESCRIPTION,
    alternates: { canonical: BASE_URL },
    metadataBase: new URL(BASE_URL),
    applicationName: APP_NAME,
    icons: {
      icon: "/pwa-assets/favicon-196.png",
      apple: "/pwa-assets/apple-icon-180.png",
    },
    manifest: "/manifest.json",
    themeColor: "#0369a1",
    appleWebApp: {
      capable: true,
      statusBarStyle: "default",
      title: APP_TITLE_TEMPLATE,
      startupImage: appleStartupImages,
    },
    twitter: {
      card: "summary",
      title: {
        default: APP_NAME,
        template: APP_TITLE_TEMPLATE,
      },
      description: APP_DESCRIPTION,
    },
  };
};
```

You can add Apple splash screens using the `startupImage` property. Here, I've created another file and an object, `appleStartupImages`, to define all the sizes of splash screens that are generated by `pwa-asset-generator`.

```ts title="data/apple-startup-images.ts"
import { AppleImage } from "next/dist/lib/metadata/types/extra-types";

export const appleStartupImages: AppleImage[] = [
	{
    url: "/pwa-assets/apple-splash-2048-2732.jpg",
    media:
      "(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)",
  },
  {
    url: "/pwa-assets/apple-splash-2732-2048.jpg",
    media:
      "(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: landscape)",
  },
  ...
]
```

---
## Step 5. Avoid committing worker, workbox files
We can prevent these automatically generated `sw.js` and `workbox-*.js` files to be committed to our repository by simply adding these lines to `.gitignore`:
```title=".gitignore"
# PWA assets and service workers
**/public/sw.js
**/public/workbox-*.js
**/public/worker-*.js
**/public/sw.js.map
**/public/workbox-*.js.map
**/public/worker-*.js.map
```