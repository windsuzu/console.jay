---
draft: false
date: 2024-06-20 18:16
tags:
  - docker
---

These commands are strongly associated with the [[Docker Container Lifecycle]].

It's recommended to use `docker stop` to stop a [[Docker Container|container]] first, instead of using `docker kill`. The `docker stop` command sends a `SIGTERM` signal to the container, allowing the container to terminate its processes gracefully and cleanly.

```bash
docker stop container_id
```

If the container doesn't stop with `docker stop` within a specified timeout period, [[Docker]] then sends a `SIGKILL` signal, which is equivalent to `docker kill` command, to the container again to force it to stop.

```bash
docker kill container_id
```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker container stop | Docker Docs](https://docs.docker.com/reference/cli/docker/container/stop/)
> - [docker container kill | Docker Docs](https://docs.docker.com/reference/cli/docker/container/kill/)