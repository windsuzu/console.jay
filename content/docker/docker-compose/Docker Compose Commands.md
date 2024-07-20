---
draft: false
date: 2024-07-20 18:16
tags:
  - docker
---

There are several commands in [[Docker Compose]] to start, stop, and list the compose.
## docker-compose up

After defining `docker-compose.yml`, we can start the containers that are defined in the `services` all at once by running:

```bash
docker-compose up
```

Sometimes you may want to rebuild all containers that use [[Dockerfile]] to build in `docker-compose.yml`. To do this, append the `--build` flag after the command:

```
docker-compose up --build
```

Additionally, if you want to run Docker Compose in the background, you can append the `-d` flag:

```
docker-compose up -d
```
## docker-compose down

When you want to shut down all the containers defined in the `docker-compose.yml`, the quickest way to do it is to use the `down` command:

```bash
docker-compose down
```

Note that when using the `down` command, you should be in the same directory as the `docker-compose.yml`. Docker Compose will automatically target the containers defined in the file and shut them down, removing any associated networks and volumes unless they are defined as external or persistent.

## docker-compose ps

Finally, you can list the services (containers) running in the docker-compose by using the `ps` command:

```bash
docker-compose ps
# NAME                       IMAGE                COMMAND                  SERVICE        CREATED       STATUS       PORTS
# simpleweb-node-app-1       simpleweb-node-app   "docker-entrypoint.s…"   node-app       2 hours ago   Up 2 hours   0.0.0.0:8080->8080/tcp
# simpleweb-redis-server-1   redis                "docker-entrypoint.s…"   redis-server   4 days ago    Up 2 hours   6379/tcp
```

Note that the `ps` command also finds `docker-compose.yml` and lists the running containers defined in that file. Therefore, you should run the `ps` command in the same directory as `docker-compose.yml`.


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [Docker Compose Quickstart | Docker Docs](https://docs.docker.com/compose/gettingstarted/)