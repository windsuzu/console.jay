---
draft: false
date: 2024-07-23 22:57
tags:
  - docker
---

> [!tip]
> You can visit [[Docker build process]] to learn the details of the Docker build and caching mechanism.

The `docker build` command takes a [[Dockerfile]] and a context (a set of files and directories located in a specific path) to build a [[Docker Image]].

```bash
docker build [options] context_path
```

In the build process, you can reference any file in the context. For example, the `COPY` instruction in the [[Dockerfile]] can reference a file in the context.

The `-t` flag is the most commonly used option for the `docker build`, which is used to tag the image with a repository name and a tag, for example, `user/project:2.0` or `organization/project:latest`.

```bash
docker build -t windsuzu/project-name:latest .

# this will automatically run the latest version
docker run windsuzu/project-name
```

The `-f` flag can be used to specify the [[Dockerfile]] you want to use to build the image. For example, sometimes you have a Dockerfile, but it is named `Dockerfile.dev` for development. If you want to build an image from that file, you can use the `-f` flag like this:

```bash
docker build -f Dockerfile.dev .
```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker build | Docker Docs](https://docs.docker.com/reference/cli/docker/image/build/)
