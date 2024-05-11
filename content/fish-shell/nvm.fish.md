---
draft: false
date: 2024-05-11 17:12
tags:
  - fish-shell
---

`nvm.fish` is the node version manager for [[fish shell]]. Using `nvm.fish` is almost the same as using [nvm](https://github.com/nvm-sh/nvm). The first thing to do is to install it with [[fisher]].

```bash
fisher install jorgebucaran/nvm.fish
```

After installing `nvm.fish`, we can list all available node versions by typing `nvm list-remote`.

```bash
# list avilable node versions
nvm list-remote
```

Then you can choose one version and install it by typing `nvm install`.

```bash
# install the latest (current) version
nvm install latest

# install LTS (long-term support) version 
nvm install lts

# install specific LTS version
nvm install lts/iron
nvm install iron

# install a specific version
nvm install v20.10.0
```

By typing `nvm list`, you can see all the versions of Node.js you've installed in your [[fish shell]].

```bash
nvm list
#   v8.17.0 lts/carbon
#   v15.3.0
#   v14.15.1 lts/fermium
#   v18.4.0 latest
# ▶ v20.13.1 lts/iron
```

Activate any version of Node.js by typing `nvm use`.

```bash
nvm use v20.13.1
```

Lastly, if you want to set the specific node version as the default, use `set --universal nvm_default_version version`.

```bash
# set lts as default version
set --universal nvm_default_version lts

# set 18.4.0 as default version
set --universal nvm_default_version v18.4.0
```

> [!info] References
> - [jorgebucaran/nvm.fish: The Node.js version manager you'll adore, crafted just for Fish (github.com)](https://github.com/jorgebucaran/nvm.fish)
