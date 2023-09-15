---
title: Create a PWA
draft: false
date: 2023-09-15 17:38
tags:
  - learning
  - pwa
---

> [!tldr] TL;DR
> 1. To start building a Progressive Web App (PWA), you need four essential files: `index.html`, a logo (preferably in SVG format), `manifest.json`, and `serviceworker.js`.
> 2. `index.html` links to `manifest.json` and registers the service worker.
> 3. Use [pwa-asset-generator](https://github.com/elegantapp/pwa-asset-generator) to automatically create icons, splash screens, and update metadata in `index.html` and `manifest.json`.
> 4. Configure the `service-worker.js` file to enable caching with [Workbox](https://github.com/GoogleChrome/workbox).
> 5. Host your PWA with `npx serve`, then test it using Google DevTools for service worker and Lighthouse audits.

## Requirements
You can start building a PWA with just four essential files: `index.html`, a logo file (preferably in SVG format), `manifest.json`, and `serviceworker.js`.

```html title="index.html" {8-9, 14-19}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    
	<!-- link manifest.json to index.html -->
    <link rel="manifest" href="manifest.json"> 
</head>
<body>
	<h1>Hello World</h1>

    <script>
	    // register service worker if supported on browser
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('./service-worker.js')
        }
    </script>
</body>
</html>
```

```json title="manifest.json"
{
    "name": "PWA Test",
    "short_name": "PWA Test",
    "start_url": "/",
    "icons": [],
    "theme_color": "#000000",
    "background_color": "#ffffff",
    "display": "fullscreen",
    "orientation": "portrait"
}
```

---
## Generating Icons and Splash Screen
The first step is to generate multiple-sized icons and a splash screen using [pwa-asset-generator](https://github.com/elegantapp/pwa-asset-generator). It automatically creates icon and splash screen images, favicons, and mstile images. Pwa-asset-generator offers a CLI tool to convert our input logo file into a bunch of icons. The usage is as follows:
```
npx pwa-asset-generator [source-file] [output-folder]
```

You can also add flags to the command. For example, use `-i` to automatically add splash screen and icon meta tags to the index file, or use `-m` to update the manifest file with the generated icons automatically.
```
npx pwa-asset-generator logo.svg -i ./index.html -m ./manifest.json
```

After running the CLI command with `-i` and `-m`, the `index.html` and `manifest.json` will be updated and filled with icon and splash screen metadata.

```html title="Updated index.html" {10,11,13}
<html>
	...
	<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Document</title>
	
    <link rel="manifest" href="manifest.json"> 
    
    <link rel="apple-touch-icon" href="icons/apple-icon-180.png">
    <meta name="apple-mobile-web-app-capable" content="yes">
    
    <link rel="apple-touch-startup-image" href="icons/apple-splash-2048-2732.jpg" media="(device-width: 1024px) and (device-height: 1366px) and (-webkit-device-pixel-ratio: 2) and (orientation: portrait)">
    ...
    </head>
	<body></body>
</html>
```

```json title="Updated manifest.json"
{
  "name": "PWA Test",
  "short_name": "PWA Test",
  "start_url": "/",
  "icons": [
    {
      "src": "icons/manifest-icon-192.maskable.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "any"
    },
    ...
  ],
  "theme_color": "#000000",
  "background_color": "#ffffff",
  "display": "fullscreen",
  "orientation": "portrait"
}
```
---
## Configure ServiceWorker
The next step is to edit our `service-worker.js` file to enable caching features for our app. We are going to import [Workbox](https://github.com/GoogleChrome/workbox) from a CDN and apply caching to the images in our app. This means that when our PWA loads an image, it will first check the cache. If the image is not in the cache, it will fetch it from the network.
```js title="service-worker.js"
importScripts("https://storage.googleapis.com/workbox-cdn/releases/6.0.2/workbox-sw.js");

workbox.routing.registerRoute(
    ({request}) => request.destination === 'image',
    new workbox.strategies.CacheFirst()
);
```
---
## Serve
Finally, you can use `npx serve` to host your PWA web app on `localhost:3000`. And now, you can open Google DevTools to test if you have managed the manifest file and started the service worker successfully. 
![[pwa-service-worker.png]]

Also, you can open the Lighthouse tool to test if your PWA audits have passed.
![[pwa-passed.png]]

> [!info] References
> - [Progressive Web Apps in 100 Seconds // Build a PWA from Scratch - YouTube](https://www.youtube.com/watch?v=sFsRylCQblw)