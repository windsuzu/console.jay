---
draft: false
date: 2024-05-19 16:30
tags:
  - fish-shell
---

Fish stands for **f**riendly **i**nteractive **sh**ell. Unlike other shells (zsh or bash), fish has built-in [syntax highlighting](https://fishshell.com/docs/current/tutorial.html#syntax-highlighting), [autosuggestions](https://fishshell.com/docs/current/tutorial.html#autosuggestions), and [tab completion](https://fishshell.com/docs/current/tutorial.html#tab-completions) with a shallow learning curve. 

After [[Install Fish Shell|installing it as your default shell]], you can basically learn everything you need to know on the official [tutorial](https://fishshell.com/docs/current/tutorial.html) page.

If you want a better theme for your fish shell, I recommend [starship](https://github.com/starship/starship). After installing starship, you can choose to customize it through [configuration](https://starship.rs/config/) or use pre-built [presets](https://starship.rs/presets/) with a single command. 

Don't forget the plugins. We can use [[fisher]] as plugin manager, and install some useful plugins, such as [[z for fish|z]], [[fzf.fish]], and [[nvm.fish]]. It's easy to use plugins in fish shell because the [tab completion](https://fishshell.com/docs/current/tutorial.html#tab-completions) shows available commands for selection, and you don't have to look up the manual all the time.

### Overview

- [[Install Fish Shell|Installation]]
- Plugins
	- [[fisher]] - plugin manager
	- [[z for fish]] - jumping around directory
	- [[fzf.fish]] - fzf (fuzzy finder) for fish
	- [[nvm.fish]] - [nvm](https://github.com/nvm-sh/nvm) (Node Version Manager) for fish
	- [done](https://github.com/franciscolourenco/done)- getting notification when process done
	- [autopair.fish](https://github.com/jorgebucaran/autopair.fish) - matching pairs `(),{},[],"",''` auto-completion



> [!info] Other useful resources 
> - [Introduction — fish-shell documentation (fishshell.com)](https://fishshell.com/docs/current/index.html#)
> - [My Fish shell workflow for coding - YouTube](https://www.youtube.com/watch?v=KKxhf50FIPI)
