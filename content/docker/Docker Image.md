---
draft: false
date: 2024-06-12 18:31
tags:
  - docker
---

A [[Docker]] Image can be thought of as a ==filesystem snapshot with a startup command==. When a [[Docker Container|container]] is created from an image, [[Docker]] first sets up a layered filesystem for the [[docker container|container]] based on the image. 

This filesystem is not loaded entirely into memory but is mounted in a way that the container can access it. [[Docker]] then executes the startup command specified in the image within this filesystem and environment.

![[docker-image.png]]


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
