---
draft: false
date: 2023-11-13 18:27
tags:
  - pwa
---

> [!tldr] TL;DR
> Progressive Web Apps (PWAs) mimic native mobile apps by offering features such as push notifications and offline mode. Advantages include the ability to install them as native apps and access to device features. To create a PWA, follow these steps: debug using Chrome tools, generate icons, create a manifest file, and implement a service worker for caching and more.

PWAs aim to provide a user experience similar to that of native mobile apps, offering features like **push notifications, offline mode, camera access, and GPS**, which web developers couldn't access before 2020.

After your web apps become PWAs, you can enjoy several key advantages:
1. PWAs can be installed as native apps.
2. PWAs can interact with device features like the camera or notifications.
3. PWAs can be published to Google Play or Microsoft Store.

You can use the following steps to [[Create a PWA]]:
1. Use the **lighthouse tool and Application tab** in Chrome Dev Tools to debug and test PWA availability.
2. Use tools like the [PWA Asset Generator](https://github.com/elegantapp/pwa-asset-generator) to create multiple-sized icons for your PWA automatically.
3. Create a `manifest.json` file containing metadata and icons for your app.
4. Implement a **service worker**, a background script that enables **caching, background sync, and push notifications**.


> [!tip] Caching Strategy
> When implementing caching strategies in your service worker, you can choose between strategies such as 'cache first' for static assets and 'network first' for dynamic content.

You may consider using libraries like [Workbox](https://github.com/GoogleChrome/workbox) to simplify PWA development. But many front-end frameworks, such as React and Angular, have built-in support for service workers. You can explore different PWA implementations in various frameworks through the [Hacker News PWA site](https://hnpwa.com/).

> [!info] References
> - [Progressive Web Apps in 100 Seconds // Build a PWA from Scratch - YouTube](https://www.youtube.com/watch?v=sFsRylCQblw)