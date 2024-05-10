---
draft: false
date: 2024-05-10 19:08
tags:
  - fish-shell
---

`z` will keep track of the directories you visit and store the calculation of each "frecency" (frequency + recency) at `$Z_DATA`. After some learning, typing `z name` will take you to the most appropriate directory whose path most closely matches `name`.

> [!tip] Use tab completion
> Provided by [[fish shell]], tab completion works seamlessly with `z`. when you press the `tab` key after typing `z ` (z and a space), fish will display available paths that were recently visited.

> [!info] References
> - [jethrokuan/z: Pure-fish z directory jumping (github.com)](https://github.com/jethrokuan/z)
