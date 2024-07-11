---
draft: false
date: 2024-07-07 17:37
tags:
  - docker
---

We can think of `Dockerfile` as a recipe for creating a new image. It contains step-by-step instructions and some other configurations for building the image. But in general, it usually contains the following key steps:

1. **Define a base image**: This step usually uses a `FROM` instruction to set a base image for subsequent instructions.
2. **Run commands to configure the image**: This step uses various instructions such as `RUN`, `ADD`, `COPY` to install dependencies, copy files, and configure env variables within the image.
3. **Specify a startup command**: This step usually uses the `CMD` instruction to define the startup command that will be executed when a container is started from the image.
## Example

The following `Dockerfile` uses `alpine` as the base image, installs `redis` for the image, and specifies to run `redis-server` whenever someone starts a container from this image.

```dockerfile title="/docker-redis/Dockerfile"
# Using an existing image as a base
FROM alpine

# Download and install redis as a dependency 
RUN apk add --update redis

# Tell the image what to do when it starts as a container
CMD [ "redis-server" ]
```

Once the `Dockerfile` is completed, we build the image with the [[docker build]] command and run the generated image using [[docker run, create, start|docker run]].

```bash title="at /docker-redis"
docker build .
# [+] Building 0.1s (6/6) FINISHED
#  => [internal] load build definition from Dockerfile
#  => => transferring dockerfile: 100B
#  => [internal] load metadata for docker.io/library/alpine:latest
#  => [internal] load .dockerignore
#  => => transferring context: 2B
#  => [1/2] FROM docker.io/library/alpine:latest
#  => CACHED [2/2] RUN apk add --update redis
#  => exporting to image
#  => => exporting layers
#  => => writing image sha256:dee0eaedf501b9b30875f44680225a44e766c727044c6c0412c1f039668508b3

docker run dee0eaed
# * Ready to accept connections tcp
```

You can visit [[Docker build process]] to learn the details of the Docker build and caching mechanism.

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [Getting docker build to show IDs of intermediate containers - Stack Overflow](https://stackoverflow.com/questions/65614378/getting-docker-build-to-show-ids-of-intermediate-containers)
