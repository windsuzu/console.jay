---
draft: false
date: 2024-06-20 18:45
tags:
  - docker
---

The `docker logs` command allows you to read the output from `STDOUT` and `STDERR` of a  a [[docker container|container]] as a batch. You can add a `-f` or `--follow` flag to stream the output from the container in real time.

```bash
docker logs [options] container_id
```

>[!example]
>
>The following example uses `docker logs` to retrieve the output of the container created with `hello-world` [[docker image|image]].
>
>```bash
>docker create hello-world
># 319297ab159e46b41a1cd580e2c02f05e40ca43f76b3fb679e478d7a6ae16c57
>
>docker start 319297ab159e46b41a1cd580e2c02f05e40ca43f76b3fb679e478d7a6ae16c57
># 319297ab159e46b41a1cd580e2c02f05e40ca43f76b3fb679e478d7a6ae16c57
>
>docker logs 319297ab159e46b41a1cd580e2c02f05e40ca43f76b3fb679e478d7a6ae16c57
># Hello from Docker!
># This message shows that your installation appears to be working correctly.
>```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker container logs | Docker Docs](https://docs.docker.com/reference/cli/docker/container/logs/)
