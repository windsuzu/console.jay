---
draft: false
date: 2024-07-26 23:10
tags:
  - docker
---

[[Docker]] volumes are a mechanism that allows us to store data outside the container on the host machine's file system. It works like mounting directories from the host machine into the container, which means that changes made to files are immediately reflected in the container.

![[docker-volumes.png]]

Volumes are often used in development workflows, allowing developers to immediately see the results in the container as they edit code on their machine. They are also used for storage, such as databases, where data needs to be preserved when the container is restarted.

## Docker Run with -v

The easiest way to use volumes is appending `-v` flag with [[docker run, create, start|docker run]] command:

```bash
docker run -v local_path:container_path image
```

For example, the following command runs the `wind/vite` image with [[docker run, create, start#Port Mapping|port mapping]] and the volume flag `-v $(pwd):/app`, which maps all the directories and files into the `/app` folder in the container.

```bash
docker run -p 3000:3000 -v $(pwd):/app wind/vite
```

## Docker compose

Another way to use volumes is through [[docker compose]]. By specifying the `volumes` keyword under the service, you can easily assign volumes to the service.

```yml
services:
  web:
    build:
      context: .
      dockerfile: Dockerfile.dev
    ports:
      - "3000:3000"
    volumes:
      - .:/app
```

For example, we specify `.:/app` in the volumes, which acts like `-v $(pwd):/app` in the `docker run` , mapping all the files to the `/app` folder in the container. 

On the right side of the colon `:`,  the `.` denotes the relative path of the host machine. On the left side, the `/app` denotes the `/app` folder in the container.

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)