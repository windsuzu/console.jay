---
draft: false
date: 2024-07-11 18:12
tags:
  - _tbd
  - docker
---

## Why

```dockerfile
FROM node:alpine

RUN npm install

CMD ["node", "start"]
```


```dockerfile
FROM node:alpine

COPY ./ ./

RUN npm install

CMD ["npm", "start"]
```

## Minimizing Cache Busting


```dockerfile
FROM node:alpine

COPY  ./

RUN npm install

COPY ./ ./


CMD ["npm", "start"]

```





> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)

