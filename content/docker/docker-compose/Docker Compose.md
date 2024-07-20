---
draft: false
date: 2024-07-20 18:16
tags:
  - docker
---

Docker compose is an useful tool that used to start **multiple services** (a.k.a. [[Docker Container|containers]]) simultaneously and place them in the same environment and network configurations.

Specifically, we need to first define the services and their configs in a YAML file (`docker-compose.yml`). After that we can start the services all at once with a single command `docker-compose up`. 

For example, if you want to launch a Dockerized Node.js application that accesses Redis in another container. You can write a `docker-compose.yml` file like below:

```yaml
services:
	redis-server:
		image: redis

	node-app:
		build: .
		ports: 
			- "8080:8080"
```

We define containers under the `services` section. In this example, we define two containers: `redis-server` and `node-app`.

The `redis-server` uses a standard container built from the `redis` [[Docker Image|image]] from [Docker Hub](https://hub.docker.com/). To use an image directly from Docker Hub or a local machine, we use the `image` keyword.

The `node-app` is a Node.js application with `redis` and `express` installed. It simply connects to the `redis-server` to retrieve, store, and display the number of visitors. Since `node-app`'s [[Dockerfile]] is in the same directory as the `docker-compose.yml`, we can use the `build` keyword to build the image from the `Dockerfile`. Finally, we set the [[docker run, create, start#Port Mapping|port mapping]] using the `ports` keyword.

>[!info]- Details of the Dockerfile
>
>```dockerfile title="Dockerfile"
> FROM node:alpine
> 
> WORKDIR /usr/app
> 
> COPY ./package.json ./
> RUN npm install
> 
> COPY ./ ./
> 
> CMD ["node", "index.js"]
> ```

>[!info]- Details of the `index.js`
>```js title="index.js"
> const express = require("express");
> const redis = require("redis");
> 
> const app = express();
> const client = redis.createClient({
>   host: "redis-server",
>   port: 6379,
> });
> 
> client.set("visits", 0);
> 
> app.get("/", (req, res) => {
>   client.get("visits", (err, data) => {
>     if (err) throw err;
>     res.send(`Number of visits is ${data}`);
>     client.set("visits", parseInt(data) + 1);
>   });
> });
> 
> app.listen(8080, () => {
>   console.log("Example app listening on port 8080!");
> });
>```

> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [Docker Compose Quickstart | Docker Docs](https://docs.docker.com/compose/gettingstarted/)