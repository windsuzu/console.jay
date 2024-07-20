---
draft: false
date: 2024-07-07 16:34
tags:
  - docker
---

![[docker-container.png]]

A [[Docker]] container is a process or a set of processes with isolated resources that are logically (not physically) allocated from the hard drive by the kernel using `namespacing` and `cgroups`. Each container has its own lifecycle, see [[Docker Container Lifecycle]] for more information.

- `namespacing` is an OS feature that segments hardware resources for specific processes. For example, creating separate segments on the hard drive for Python 2 and Python 3, and directing system calls to the appropriate segment based on which application is making the call.
- `cgroups` (Control Groups) limit the amount of resources (CPU, memory, network bandwidth) a process can use.


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)