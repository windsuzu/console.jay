---
title: Chart.js
draft: false
date: 2023-10-07 00:18
tags:
  - chart-js
---

Chart.js is a widely-used charting library for JavaScript developers, boasting approximately 60,000 [GitHub stars](https://github.com/chartjs/Chart.js) and around 2,400,000 weekly [npm downloads](https://www.npmjs.com/package/chart.js) as of October 2023. It not only provides default [chart types](https://www.chartjs.org/docs/latest/charts/area.html) with a variety of [plugins](https://github.com/chartjs/awesome#plugins), configurations, and animations but also offers numerous additional [community-maintained chart types](https://github.com/chartjs/awesome#charts). Furthermore, it is possible to combine several chart types into a [mixed chart](https://www.chartjs.org/docs/latest/charts/mixed.html).

In addition to its well-maintained, easy-to-use, and out-of-the-box functionalities, Chart.js offers two compelling advantages that users appreciate: a developer-friendly experience and high performance.

For developer experience, Chart.js includes built-in TypeScript typings and is compatible with [[react-chartjs-2|React]], Vue, Svelte, and Angular. Furthermore, Chart.js offers comprehensive [documentation](https://www.chartjs.org/docs/latest/), an extensive [API reference](https://www.chartjs.org/docs/latest/api/), and a variety of [examples](https://www.chartjs.org/docs/latest/samples/information.html). Developers can also find numerous solved questions on Stack Overflow tagged with `chart.js`.

For performance, Chart.js renders chart elements on an HTML5 canvas instead of as SVG, which can require managing thousands of SVG nodes in the DOM tree. This approach makes Chart.js well-suited for handling large datasets, even without the need for [data parsing and normalization](https://www.chartjs.org/docs/latest/general/performance.html). Additionally, developers have the option to implement [data decimation](https://www.chartjs.org/docs/latest/configuration/decimation.html) to sample the dataset and reduce the chart's size before rendering. Chart.js also supports tree-shaking, allowing you to further reduce the bundle size.

> [!info] References
> - [Chart.js | Chart.js (chartjs.org)](https://www.chartjs.org/docs/latest/)
