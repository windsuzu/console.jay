---
draft: false
date: 2023-11-13 18:26
tags:
  - chart-js
---

You can apply tree-shaking for [[Chart.js]] when you [[Getting Started with Chart.js|finish development]] and ready to push your project to production. Tree-shaking is a term for removing unused code from the JavaScript bundle.

When we build the project without tree-shaking, which implies that we imported all available components from `"chart.js/auto"`, we receive the following bundle result:
```bash
> chartjs-example@1.0.0 build
> parcel build src/index.html

✨ Built in 7.05s

dist\index.html              313 B    5.26s
dist\index.7311b552.js    209.1 KB    964ms
```

To achieve tree-shaking is simple. We only need to replace `import Chart from "chart.js/auto";` with the following method of importing only the necessary components to create our chart.
```js
import {
  Chart,
  BarController,
  CategoryScale,
  LinearScale,
  BarElement,
  Colors,
  Legend,
} from "chart.js";

Chart.register(
  BarController,
  CategoryScale,
  LinearScale,
  BarElement,
  Colors,
  Legend,
);
```
And the result shows our bundle size is reduced.
```bash
> chartjs-example@1.0.0 build
> parcel build src/index.html

✨ Built in 2.58s

dist\index.html               313 B    832ms
dist\index.e65aa5c3.js    197.19 KB    634ms
```

> [!tip]
> If you don't know which components you need for creating your chart, you can open the browser console and learn from the warning message, such as:
> ```
> Unhandled Promise Rejection: Error: "bar" is not a registered controller.
> ```

> [!info] References
> - [Step-by-step guide - Tree-shaking | Chart.js (chartjs.org)](https://www.chartjs.org/docs/latest/getting-started/usage.html#tree-shaking)
