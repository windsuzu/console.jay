---
draft: false
date: 2024-05-09 18:10
tags:
  - fish-shell
---

## Installation

You can find instructions for installing [[fish shell]] on all different operating systems [on the official homepage](https://fishshell.com/). In my case, I'm using WSL 2 on Windows. So, I have to install WSL 2 first and choose Ubuntu instructions because that’s my main OS for WSL 2.

```bash title="Installation command (used 2024/05)"
sudo apt-add-repository ppa:fish-shell/release-3  
sudo apt update  
sudo apt install fish
```

## Set Fish as default shell

If your [[fish shell]] is installed at `/usr/local/bin/fish` (you can check it using `command -s fish`), you can just paste this path into your terminal app (e.g., Mac Terminal, Windows Terminal, GNOME Terminal) to start fish directly.

If you want to set fish as your default login shell, here’s what you need to do.

> [!warning]
> Before you run the following commands, it's a good idea to check the correct path for your [[fish shell]] by running `command -s fish`.

```bash
# Add the shell to etc/shells
echo /usr/local/bin/fish | sudo tee -a /etc/shells

# change the default shell
chsh -s /usr/local/bin/fish
```

If you want to switch back to another shell, just replace `/usr/local/bin/fish` with the path to another shell. For example, `/bin/bash`, `/bin/tcsh` or `/bin/zsh`.

> [!info] References
> - [Introduction — fish-shell 3.7.0 documentation (fishshell.com)](https://fishshell.com/docs/current/#installation)
> - [fish shell](https://fishshell.com/)
