---
draft: false
date: 2024-07-09 16:20
tags:
  - docker
---

Alpine in [[Docker]] refers to any [[Docker Image|image]] is built on top of a small (around 5 MB), lightweight, and security-oriented Linux distribution called [Alpine Linux](https://alpinelinux.org/).

## Alpine Linux Image

At the very beginning, there is an image that inherits the features of Alpine Linux which can be imported as `alpine` in a [[Dockerfile]]. The Dockerfile below creates an image using Alpine Linux, and installs the bash shell, and runs it whenever the container is created and run.

```Dockerfile
FROM alpine

RUN apk add --no-cache bash

CMD ["bash"]
```

>[!tip]
>Adding `--no-cache` prevents the `apk` from storing index cache files locally. This can both reduce the image size and ensure that the latest dependency is always installed.

## Node Alpine Image

Node.js [[Docker Image|Docker images]] also have variants that use the Alpine Linux image as their base image. These images are tagged with `alpine`, such as `node:alpine`, which uses Alpine Linux with the **current** version of Node, or `node:lts-alpine`, which uses Alpine Linux with the stable **LTS** version of Node.

The following [[Dockerfile]] uses `lts-alpine` as the base image and runs a basic Node.js application whenever the container is created from the image.

```Dockerfile
# Use the Node.js image based on Alpine Linux with the LTS version of Node.js
FROM node:lts-alpine

# Set the working directory
WORKDIR /app

# Copy the package.json file and install dependencies
COPY package.json .
RUN npm install

# Copy the rest of the application files
COPY . .

# Set the command to run the application
CMD ["node", "index.js"]
```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
