---
draft: false
date: 2024-05-11 18:18
tags:
  - fish-shell
---

[fzf](https://github.com/junegunn/fzf) is a powerful fuzzy finder that provides a user interface to search the directory, command history, and git status and log. 

[fzf.fish](https://github.com/PatrickF1/fzf.fish) provides some default key bindings and makes it easier for you to customize the key bindings and functionalities of [fzf](https://github.com/junegunn/fzf). 

### Search directory

To search the directory, press `Alt` + `Ctrl` + `F` (you won't see the files in `.gitignore`). When you hit `Enter` on a file or directory, the **relative path** will show up in the input. If the path is a directory, you can just hit `Enter` again to get the same result as `cd` to it.  

### Search command history

To search the command history, just press `Ctrl` + `R`. When you hit `Enter` on the previous command, the one you selected will show up in the input field.

### Search Git

- Press `Alt` + `Ctrl` + `S` for searching git status.
- Press `Alt` + `Ctrl` + `L` for searching git log.


> [!info] References
> - [junegunn/fzf: :cherry_blossom: A command-line fuzzy finder (github.com)](https://github.com/junegunn/fzf)
> - [PatrickF1/fzf.fish: 🔍🐟 Fzf plugin for Fish (github.com)](https://github.com/PatrickF1/fzf.fish)
