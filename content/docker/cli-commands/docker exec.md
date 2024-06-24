---
draft: false
date: 2024-06-24 17:46
tags:
  - docker
---

The command is strongly associated with the [[Docker Container Lifecycle]].

The `docker exec` command allows you to interact with a running [[docker container|container]] or enter its shell. It is commonly used with the `-it` [[Docker -it flags|flags]] to enable interaction with the container's input and output streams.

```bash
docker exec [options] container_id command
```

>[!example]
>In the following example, we will start by running a container with the `redis` [[docker image|image]]. This will create a container that will initially run `redis-server`.
>
>```bash title=terminal 1
>docker run redis
># * monotonic clock: POSIX clock_gettime
># * Running mode=standalone, port=6379.
># * Server initialized
># * Ready to accept connections tcp
>```
>To use the `redis` functionality, we need to run `redis-cli` in the container shell and its environment. To do this, we create another terminal and check the `continer_id` using [[docker ps]]. Then we use `docker exec -it` with the retrieved `container_id` to call `redis-cli` in the container.
>
>```bash title=terminal 2
>docker ps
># CONTAINER ID   IMAGE     COMMAND                  CREATED              STATUS              PORTS      NAMES
># 408ff5ce70cb   redis     "docker-entrypoint.s…"   About a minute ago   Up About a minute   6379/tcp   nice_dhawan
>
>docker exec -it 408ff5ce70cb redis-cli
>127.0.0.1:6379> set number 1
># OK
>127.0.0.1:6379> get number
># "1"
>```
>
>![[docker-exec-redis.png]]

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker exec | Docker Docs](https://docs.docker.com/reference/cli/docker/container/exec/)
