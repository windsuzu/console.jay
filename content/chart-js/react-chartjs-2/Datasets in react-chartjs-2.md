---
title: Datasets in react-chartjs-2
draft: false
date: 2023-10-07 00:18
tags:
  - chart-js
  - react-chartjs-2
---

You may encounter a problem where certain events, such as hover tooltips, inadvertently trigger the merging of datasets in a chart. This issue occurs because the library requires a unique key to track changes in dataset series, and in the absence of such a key, it cannot distinguish between datasets during updates.

To address the problem, you have two possible solutions:
1. Add a `label` to each dataset. [[react-chartjs-2]] uses the `label` property as the default key to distinguish datasets.

```js title="Add label" {5,11}
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

2.  You can specify a different property to be used as a key by passing a `datasetIdKey` prop to your chart component.

```js title="Add datasetIdKey" {19}
const data: ChartData<"line"> = {
  labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
  datasets: [
    {
      label: "",
      data: [12, 19, 3, 5, 2, 3],
      borderColor: "rgb(255, 99, 132)",
      backgroundColor: "rgba(255, 99, 132, 0.5)",
    },
    {
      label: "",
      data: [2, 3, 20, 5, 1, 4],
      borderColor: "rgb(54, 162, 235)",
      backgroundColor: "rgba(54, 162, 235, 0.5)",
    },
  ],
};

<Line data={data} options={options} datasetIdKey="borderColor" />
```

> [!info] References
> - [Working with datasets | react-chartjs-2](https://react-chartjs-2.js.org/docs/working-with-datasets)
