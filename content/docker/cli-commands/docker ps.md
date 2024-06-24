---
draft: false
date: 2024-06-24 17:19
tags:
  - docker
---

The command is strongly associated with the [[Docker Container Lifecycle]].

The `docker ps` (short for `docker container ls`) command allows you to check the `CONTAINER_ID`, `IMAGE_NAME`, `COMMAND`, `CREATED_TIME`, `STATUS`, `PORTS`, and `NAME` of the running container.

```bash
docker ps [options]
```

>[!example]
>You can add an `-a` or `-all` flag to `docker ps` to show information about all containers you've run before. Without this flag, you will only see the currently running containers.
>
>```bash
>docker ps -a
>```

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker ps | Docker Docs](https://docs.docker.com/reference/cli/docker/container/ls/)
