---
draft: false
date: 2024-07-15 17:10
tags:
  - docker
---

>[!info] 
>Starting Node.js 15, if there is no `WORKDIR` specified in the [[Dockerfile]], `npm install` running in the root of the container will cause an error!

The `WORKDIR` instruction in the [[Dockerfile]] works like `cd` in Linux, and also sets the current working directory to the specified path.

```dockerfile
WORKDIR working_directory_path_in_container
```

For example, the [[Dockerfile]] below sets `WORKDIR` to `/usr/app` relative to the root of the container. So the `package.json` is copied from the local machine context to `/usr/app`, and `npm install` is run in `/usr/app`.

Finally, all files are copied to `/usr/app`, and the [[docker container|container]] will run `node index.js` by default in `/usr/app` when it is built from the [[docker image|image]].

```dockerfile {3}
FROM node:alpine

WORKDIR /usr/app

COPY ./package.json ./
RUN npm install

COPY ./ ./

CMD ["node", "index.js"]
```

The benefits of `WORKDIR` are as follows:

- **Readability and Maintainability**: Don't need to specify absolute paths in each command
- **Consistency**: Ensures that all commands operate in the same directory
- **Optimized Caching**: Leverages Docker's layer caching more effectively
- **Default Working Directory for CMD**: Ensures that your application starts in the correct directory


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [dockerfile - npm ERR! Tracker "idealTree" already exists while creating the Docker image for Node project - Stack Overflow](https://stackoverflow.com/questions/57534295/npm-err-tracker-idealtree-already-exists-while-creating-the-docker-image-for)
