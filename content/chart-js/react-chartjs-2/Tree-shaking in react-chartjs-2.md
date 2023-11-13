---
draft: false
date: 2023-11-13 18:26
tags:
  - chart-js
  - react-chartjs-2
---

There are three different ways to import dependencies in [[react-chartjs-2]] before creating our chart:
1. The laziest way - import all dependencies from [[Chart.js]].
2. The tree-shakable way - import only what is needed for the specific chart.
3. The tree-shakable typed chart components - no need for a controller.

```tsx title="lazy way" {1}
import 'chart.js/auto';  
import { Chart } from 'react-chartjs-2';  
  
<Chart type='line' data={chartData} />
```

When you use `Chart` as your chart component, it's almost the same way to implement [[Tree-shaking of Chart.js|tree-shaking in native Chart.js]].

```tsx title="tree-shakable way" {10,12,22,25}
import {
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Legend,
  Tooltip,
  Chart as ChartJS,
  LineController,
} from "chart.js";
import { Chart } from "react-chartjs-2";

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Legend,
  Tooltip,
  LineController
);

<Chart type="line" data={data} options={options} />
```

When you use `Line` or any other chart component instead of `Chart`, you can simply omit the import of its controller. For example, there's no need to register `LineController` when you use `Line` instead of `Chart`.

```tsx title="typed chart components" {11,23}
import {
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Legend,
  Tooltip,
  Chart as ChartJS,
} from "chart.js";
import { Line } from "react-chartjs-2";

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Legend,
  Tooltip,
);

<Line data={data} options={options} />
```

> [!info] References
> - [Migration to v4 | react-chartjs-2](https://react-chartjs-2.js.org/docs/migration-to-v4#tree-shaking)
