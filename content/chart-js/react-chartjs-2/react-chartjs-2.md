---
title: react-chartjs-2
draft: false
date: 2023-10-03 15:26
tags:
  - learning
  - chart-js
  - react-chartjs-2
---

[react-chartjs-2](https://github.com/reactchartjs/react-chartjs-2) is a React component library for [[Chart.js]] that provides a component-based approach to [[Getting Started with Chart.js|create charts]] using [[Chart.js]]. It also offers features such as [[Plugins of Chart.js|plugins]] and [[Tree-shaking of Chart.js|tree-shaking of Chart.js]].

Let's create a project using Vite and try installing `react-chartjs-2`:
```bash
yarn create vite
yarn install
yarn add react-chartjs-2 chart.js
```
  
We are using version 4.4.0 of [[chart.js]] and version 5.2.0 of `react-chartjs-2`.
```json title="package.json"
"dependencies": {
    "chart.js": "^4.4.0",
    "react-chartjs-2": "^5.2.0",
  }
```

You can easily create a chart by following the [examples in the react-chartjs-2 documentation](https://react-chartjs-2.js.org/examples). Let's create a line chart in 3 steps: generate datasets, define an options object, and place them into a `Line` component.

Defining datasets is very similar to using native [[Chart.js]]. You can learn more about constructing data structures from the [official documentation](https://www.chartjs.org/docs/latest/general/data-structures.html).

```tsx title="dataset"
import type { ChartData, ChartOptions } from "chart.js";

const data: ChartData<"line"> = {
  labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
  datasets: [
    {
      label: "Dataset 1",
      data: [12, 19, 3, 5, 2, 3],
      borderColor: "rgb(255, 99, 132)",
      backgroundColor: "rgba(255, 99, 132, 0.5)",
    },
    {
      label: "Dataset 2",
      data: [2, 3, 20, 5, 1, 4],
      borderColor: "rgb(54, 162, 235)",
      backgroundColor: "rgba(54, 162, 235, 0.5)",
    },
  ],
};
```

You can also use all the flexible options from the native [[Chart.js]]'s APIs with `react-chartjs-2`.

```tsx title="options"
const options: ChartOptions<"line"> = {
  responsive: true,
  plugins: {
    legend: { position: "bottom" },
    title: {
      display: true,
      text: "Chart.js Line Chart",
      font: { size: 24 },
    },
  },
};
```

The only remaining task is to provide the `data` and `options` to the `Chart` component. In this case, we are using `Line` as our Chart component.

```tsx title="place data and options into Line"
import "chart.js/auto";
import { Line } from "react-chartjs-2";

const App = () => (
  <main>
    <Line data={data} options={options} />
  </main>
);
```

You can achieve the following result. However, there are some issues and improvements to consider:

1. [[Tree-shaking in react-chartjs-2|Implementing tree-shaking with react-chartjs-2.]]
2. [[Datasets in react-chartjs-2|Being cautious about the keys used in datasets.]]

![[react-chart-js-2.png]]

> [!info] References
> - [react-chartjs-2 | react-chartjs-2](https://react-chartjs-2.js.org/)
> - [Line Chart | react-chartjs-2](https://react-chartjs-2.js.org/examples/line-chart)
