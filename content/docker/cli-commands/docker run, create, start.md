---
draft: false
date: 2024-06-18 18:24
tags:
  - docker
---

These commands are strongly associated with the [[Docker Container Lifecycle]].
## docker run

The `docker run` command asks the [[Docker]] server to "create" and "start" a container based on the given [[docker image|image]]. If the image is not found on the local machine, server will retrieve it from the [[Docker]] Hub first.

```bash
docker run [options] image_name [command]
```

>[!example]
> The following example pulls the `busybox` image from the [[Docker]] Hub, then creates and starts a container with it. It also specifies a shell to be started inside the container and the `-i` and `-t` [[Docker IT flags|flags]] to interact directly with the shell in the container.
> 
>```bash
>docker run -it busybox sh
>```
>
>PS. `busybox` is a tiny (<5Mb) image that combines many common UNIX utilities into a single executable for crafting space-efficient distributions.

## docker create

The `docker create` command takes an [[docker image|image]] and creates a new [[docker container|container]] without running it. It then prints the `container_id` for further operations. You can specify a **startup command** for this container at the time of creation, which will be executed each time the container is started.

```bash
docker create [options] image_name [command]
```

>[!example]
> The following example creates a new container from the `busybox` image and assigns a startup command of `echo hello`.
>
>```bash
>docker create busybox echo hello
># 610ea68044541a3b4e2bac5ca889b6978e1fa529dd5c96199aeeb11b9b9b5765
>```

## docker start

The `docker start` simply starts the [[docker container|container]] we created with `docker create`, or restarts the [[docker container|container]] that was already finished and stopped.

```
docker start [options] container_id
```

>[!example]
>The following example starts the `busybox` container with the command `echo hello`. We also append an `-a` flag to display the output of the container. 
>```bash
>docker start -a 610ea68044541a3b4e2bac5ca889b6978e1fa529dd5c96199aeeb11b9b9b5765
># hello
>```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker container create | Docker Docs](https://docs.docker.com/reference/cli/docker/container/create/)
> - [docker container start | Docker Docs](https://docs.docker.com/reference/cli/docker/container/start/)
> - [docker run | Docker Docs](https://docs.docker.com/reference/cli/docker/container/run/) 
> - [busybox - Official Image | Docker Hub](https://hub.docker.com/_/busybox)
