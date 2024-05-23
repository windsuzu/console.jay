---
draft: false
date: 2024-05-23 20:21
tags:
  - prettier
---

Prettier is a code formatter that helps you format your code into a consistent rule or specification. This is useful if you're working with team members. You may want to share a rule for formatting the code. 

Prettier can be very powerful when used in your editor, especially if you use it in Visual Studio Code, you can install the [prettier-vscode](https://github.com/prettier/prettier-vscode), an extension for Prettier, and use format on save to get format automatically every time you hit save.

If you are using a linter like ESLint, there may be some trivial linting errors that can be easily formatted and fixed by Prettier. Therefore, you can use something like [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) to disable those unnecessary rules that might conflict with Prettier.

If you are using Tailwind, [prettier-plugin-tailwindcss](https://github.com/tailwindlabs/prettier-plugin-tailwindcss) provides a wonderful feature for you to sort the tailwind class names in an [official recommended class order](https://tailwindcss.com/blog/automatic-class-sorting-with-prettier#how-classes-are-sorted).

> [!info] References
> - [Prettier · Opinionated Code Formatter](https://prettier.io/)
> - https://github.com/prettier/prettier-vscode
