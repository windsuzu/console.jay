---
draft: false
date: 2024-06-15 16:04
tags:
  - docker
---

When a Docker container is created with `docker create`, it can be started using `docker start` multiple times (you can also use the `docker run` command to create and start a container simultaneously). The container may run and finish immediately or run for an extended duration, depending on the processes it executes. Once a container has been started and stopped, you can start it again using `docker start` as long as it hasn't been removed.




When container is running, you can stop or kill it. When container is stopped, you can start it again with start or exec command, you can also remove the container from the memory in the local machine using container prune command.



> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
