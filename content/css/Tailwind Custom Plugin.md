---
draft: false
date: 2023-12-01 17:37
tags:
  - css
  - tailwind
---

Tailwind provides a `plugin` function as an exposed API for customizing reusable styles. The `plugin` function can be imported from the `tailwindcss/plugin` module and invoked in the `plugins` array in the `tailwind.config.js`.

In this note, we will create a reusable neon effect style that can be easily applied using the classname `neon-*` with different colors. For example, the div box below implements a vibrant `box-shadow` style by simply using the classname `neon-amber` or by using `neon-primary` if you declare the primary color in the `theme > extends > colors` object in `tailwind.config.js`.

```tsx title="App.tsx"
const App = () => (
  <div className="p-8 rounded-md neon-primary">
    <h1 className="text-3xl font-bold">Hello world!</h1>
  </div>
);
```

![[tailwind-custom-plugin-result.png]]

## Implementation

The plugin function receives an argument that can be destructured into several helper functions. In our example, we are going to use only two of those functions, namely `theme` and `addUtilities`. You can view all the helper functions in the [Tailwind official documentation](https://tailwindcss.com/docs/plugins).

- `theme()` retrieves styles from Tailwind's default theme. In our case, we are going to retrieve all the colors from the default theme.
- `addUtilities()` can be used to register our own static styles.

```js title="tailwind.config.js"
const plugin = require('tailwindcss/plugin');
const colors = require('tailwindcss/colors');

const neonPlugin = plugin(({ theme, addUtilities }) => {
  const colors = theme('colors');
  const neonUtilities = {};

  for (const color in colors) {
    /*
    * The colors
    */
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

Now, if you are using the [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) extension in your VSCode, you will see our `neon-*` classnames appearing in the auto-complete suggestions.

![[tailwind-custom-plugin-intellisense.png]]

> [!info] References
> - [10 Tailwind Tricks You NEED To Know! - YouTube](https://www.youtube.com/watch?v=aSlK3GhRuXA)
> - [Plugins - Tailwind CSS](https://tailwindcss.com/docs/plugins)
