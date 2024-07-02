---
draft: false
date: 2024-07-02 18:44
tags:
  - docker
---

The `docker commit` command helps us to create a new [[Docker Image|image]] from a running container's current state. It's useful to quickly create an ad-hoc image for debugging, rather than creating a general image from a [[Dockerfile]] and the [[docker build]] command.

```bash
docker commit [options] container_id [repository:tag]
```

### Example

To create a new image using `docker commit`, you must first create a running container. Below, we will create a container with the `alpine` image, then install `redis` into the container.

```bash
docker run -it alpine sh
> apk add --update redis

# fetch https://dl-cdn.alpinelinux.org/alpine/v3.20/main/x86_64/APKINDEX.tar.gz
# fetch https://dl-cdn.alpinelinux.org/alpine/v3.20/community/x86_64/APKINDEX.tar.gz
# (1/1) Installing redis (7.2.5-r0)
# Executing redis-7.2.5-r0.pre-install
# Executing redis-7.2.5-r0.post-install
# Executing busybox-1.36.1-r29.trigger
# OK: 11 MiB in 15 packages
```

Now the container `0cd8e31b9e53` is running with `redis` installed. We can now create a new image, give it a startup command (`CMD ["redis-server"]`) using the `-c` flag, and assign a repository name and tag (`test/redis:latest`) to it using `docker commit`.

```bash
docker ps
# CONTAINER ID   IMAGE     COMMAND   CREATED          STATUS          PORTS     NAMES
# 0cd8e31b9e53   alpine    "sh"      38 seconds ago   Up 37 seconds             determined_jang

docker commit -c 'CMD ["redis-server"]' 0cd8 test/redis:latest
# sha256:5547e8d00f17fce045236b375edcd951a12af9b4987b285edf4f183c09bd9e22

docker images
# REPOSITORY    TAG       IMAGE ID       CREATED              SIZE
# test/redis    latest    5547e8d00f17   3 seconds ago        13.7MB

docker run test/redis
# * monotonic clock: POSIX clock_gettime
# * Running mode=standalone, port=6379.
# * Server initialized
# * Ready to accept connections tcp
```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker container commit | Docker Docs](https://docs.docker.com/reference/cli/docker/container/commit/)
