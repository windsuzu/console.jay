---
draft: false
date: 2024-07-15 16:54
tags:
  - docker
---

```dockerfile
COPY from_context_path to_container_path
```

Although the [[Dockerfile]] is run and built on a given context path to build an [[docker image|image]], no files are mirrored to the corresponding [[docker container]] environment.

![[docker-container-no-files.png]]

From the above example, when we run `npm install` inside the container, the `package.json` does not exist inside the container. So the `npm install` will fail.

Therefore, before the `npm install`, we can use the `COPY` instruction to copy all the files from the **relative context path (first argument)** to **the container path (second argument)**.

```dockerfile {5}
FROM node:alpine

WORKDIR /usr/app

COPY ./ ./

RUN npm install

CMD ["npm", "start"]
```

## Minimizing Cache Busting

If you know that [[Docker]] can [[Docker build process#Caching|cache build processes]], you will notice that `COPY ./ ./` is not a plausible way to copy files into the container. This is because every time you change a file or even a single character in your project, the instructions after `COPY ./ ./` will be rebuilt without caching. Therefore, the `npm install` will drag the whole build process every time you build.

```dockerfile {5}
FROM node:alpine

WORKDIR /usr/app

COPY  ./package.json ./

RUN npm install

COPY ./ ./

CMD ["npm", "start"]

```

A preferred way to copy files into the container is to first copy the `package.json` or other package management files in different languages and run the dependency install.

This ensures that `npm install` is only rebuilt when there are changes in `package.json` and saves us a lot of time. 

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)

