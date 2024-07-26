---
draft: false
date: 2024-07-26 23:26
tags:
  - docker
---

In [[Dockerfile]], we can separate the workflow and virtual memory space in the container using multi-step builds. Multi-step builds use the `FROM` and `AS` keywords to specify and generate a new step and workspace that is isolated from the other stages. 

It can help us build a smaller final image by leaving dependencies in intermediate steps. It can also increase security and optimize build performance.

```dockerfile
FROM node:20-alpine AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build


FROM nginx:stable-alpine AS runner
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
```

The example above shows a multi-stage build with two stages: `builder` and `runner`. In the `builder` stage, we use `Node.js alpine` as the base image to install and build the application. 

This is followed by the `runner` stage, where we use another image `nginx` to build the nginx server, copy the built application from `/app/dist` of the `builder` stage to `/usr/share/nginx/html` of the `runner` stage, and expose port 80 for the nginx server.


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
