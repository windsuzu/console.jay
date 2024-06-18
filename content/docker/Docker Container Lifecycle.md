---
draft: false
date: 2024-06-18 18:24
tags:
  - docker
---

![[docker-container-lifecycle.png]]
> Source: [Docker Container Lifecycle Management](https://k21academy.com/docker-kubernetes/docker-container-lifecycle-management/)

When a [[Docker]] container is created with `docker create`, it can be started using `docker start` multiple times (you can also use the `docker run` command to create and start a container simultaneously).  The container may run and finish immediately or run for an extended duration, depending on the processes it executes. 

>[!seealso] 
>- [[docker run, create, start]]

When the container is running, you can either stop it using `docker stop`, kill it using `docker kill`, or run additional commands inside the container's environment using `docker exec`, which is a way to interact with the container while it's running.

>[!seealso] 
>- [[docker stop, kill]]

Once a container has completed its processes and stopped, you can restart it with `docker start`, as long as it hasn't been removed. If you want to remove the container from your machine, you can use `docker container prune` to remove all non-running containers.


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
