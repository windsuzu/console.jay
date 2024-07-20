---
draft: false
date: 2024-06-24 18:16
tags:
  - docker
---

The command is strongly associated with the [[Docker Container Lifecycle]].

Under the hood, all [[Docker Container|containers]] are running in a Linux-based environment that [[Docker]] provides. Therefore, every container has three channels handling input, output, and error; namely, `STDIN`, `STDOUT`, and `STDERR`.

When we want to interact with a container with its shell, in order to input something and get a user-friendly interface with features like auto-suggestions, we need to connect our terminal with the container's `STDIN` using the `-i` flag, and with the container's `STDOUT` and `STDERR` using the `-t` flag. That's why we need to add the combined `-it` (`-i` and `-t`) flags when running [[docker run, create, start|docker run]] or [[docker exec]].

![[continer-input-output.png]]

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
