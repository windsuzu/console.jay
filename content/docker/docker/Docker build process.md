---
draft: false
date: 2024-07-15 16:04
tags:
  - docker
---

To further understand the details of the build process when building a [[Dockerfile]], we can run [[docker build]] without `buildkit` to see the output logs differently.

```bash
DOCKER_BUILDKIT=0 docker build .
```

>[!note]
 After version 18.09, we use `DOCKER_BUILDKIT=0` to temporarily disable [buildkit](https://github.com/moby/buildkit) to see more details during the build process.  

Below is the output of the build process when building a `Dockerfile` for the first time. You can see that there are encoded ids like `a606584aa9aa`, `16c286ae3e39`, `2348ec2e0d16`, etc. These ids represent layers and temporary containers.

```bash {3,7,17-18,22-25}
# Sending build context to Docker daemon  2.048kB
# Step 1/3 : FROM alpine
#  ---> a606584aa9aa


# Step 2/3 : RUN apk add --update redis
#  ---> Running in 16c286ae3e39
# fetch https://dl-cdn.alpinelinux.org/alpine/v3.20/main/x86_64/APKINDEX.tar.gz
# fetch https://dl-cdn.alpinelinux.org/alpine/v3.20/community/x86_64/APKINDEX.tar.gz
# (1/1) Installing redis (7.2.5-r0)
# Executing redis-7.2.5-r0.pre-install
# Executing redis-7.2.5-r0.post-install
# Executing busybox-1.36.1-r29.trigger
# OK: 11 MiB in 15 packages
#  ---> Removed intermediate container 16c286ae3e39
#  ---> 2348ec2e0d16


# Step 3/3 : CMD [ "redis-server" ]
#  ---> Running in e1bf177949e0
#  ---> Removed intermediate container e1bf177949e0
#  ---> 6bb3356302a2
# Successfully built 6bb3356302a2
```

Each step or instruction of `Dockerfile`, such as `FROM`, `RUN`, `CMD`, is running in its own isolated environment, creating a new layer. 

Except for `FROM`, when a step is executed, [[Docker]] creates a new [[Docker Container|container]] using the [[Docker Image|image]] from the previous layer. For example, step 2 created a temporary container `16c286ae3e39` from the previous layer's image `a606584aa9aa`. 

When the process was completed in one step, Docker removed the temporary container and saved the changes as a new layer in the new image. For example, `16c286ae3e39` is removed and `2348ec2e0d16` is created at the end of the step 2.

![[docker-build-process-example.png]]
## Caching

Docker uses the images created in each layer as caches to speed up the build process. If a step hasn't changed (including the order), Docker can reuse the cached layer from the previous build.

```bash
DOCKER_BUILDKIT=0 docker build .
```

```bash
# Sending build context to Docker daemon  2.048kB
# Step 1/3 : FROM alpine
#  ---> a606584aa9aa
# Step 2/3 : RUN apk add --update redis
#  ---> Using cache
#  ---> 2348ec2e0d16
# Step 3/3 : CMD [ "redis-server" ]
#  ---> Using cache
#  ---> 6bb3356302a2
# Successfully built 6bb3356302a2
```

![[docker-build-process-cache.png]]


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> -  [Getting docker build to show IDs of intermediate containers - Stack Overflow](https://stackoverflow.com/questions/65614378/getting-docker-build-to-show-ids-of-intermediate-containers)