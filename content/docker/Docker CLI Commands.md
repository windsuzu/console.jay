---
draft: false
date: 2024-06-15 15:41
tags:
  - docker
---



## run

The `run` command from the CLI asks the [[Docker]] server to "create" and "start" a container based on the given [[docker image|image]]. If the image is not found on the local machine, server will retrieve it from the [[Docker]] Hub first.

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

## create


## start


## ps
## exec
## stop and kill

## container prune

## logs





> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [busybox - Official Image | Docker Hub](https://hub.docker.com/_/busybox)
