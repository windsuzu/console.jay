---
draft: false
date: 2023-12-01 16:51
tags:
  - css
  - tailwind
---



```js title="tailwind.config.js"
const plugin = require('tailwindcss/plugin');
const colors = require('tailwindcss/colors');

const neonPlugin = plugin(({ theme, addUtilities }) => {
  const colors = theme('colors');
  const neonUtilities = {};

  for (const color in colors) {
    if (typeof colors[color] === 'object') {
      const shades = colors[color];
      neonUtilities[`.neon-${color}`] = {
        boxShadow: `0 0 5px ${shades['500']}, 0 0 20px ${shades['700']}`,
      };
    }
  }

  addUtilities(neonUtilities);
});

/** @type {import('tailwindcss').Config} */
export default {
  content: ['./index.html', './src/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {
      colors: {
	    // you can change the primary color here
        primary: colors.amber,
      },
    },
  },
  plugins: [neonPlugin],
};

```

```tsx title="App.tsx"
const App = () => (
  <div className="p-8 rounded-md neon-primary">
    <h1 className="text-3xl font-bold">Hello world!</h1>
  </div>
);
```
![[tailwind-custom-plugin-intellisense.png]]
![[tailwind-custom-plugin-result.png]]


> [!info] References
> - [10 Tailwind Tricks You NEED To Know! - YouTube](https://www.youtube.com/watch?v=aSlK3GhRuXA)
> - [Plugins - Tailwind CSS](https://tailwindcss.com/docs/plugins)
