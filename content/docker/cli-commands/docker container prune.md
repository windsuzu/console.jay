---
draft: false
date: 2024-06-24 17:19
tags:
  - docker
---

The command is strongly associated with the [[Docker Container Lifecycle]].

The `docker container prune` will get your confirmation and remove all stopped containers from your local machine.

```bash
docker container prune

# WARNING! This will remove all stopped containers.
# Are you sure you want to continue? [y/N] y

# Deleted Containers:
# 610ea68044541a3b4e2bac5ca889b6978e1fa529dd5c96199aeeb11b9b9b5765
# 65ed6cd1dfba08a177fcdead54133071c85280e5a73311c86300e967a4fa9c23
# 3f0e22ece1bf45ddb0ba2e5a02ea61bf2508a31f4f3fadc1987b14b97f500f72
# 01fcc6eb224d745d16e52055e5a643a9bdeea0de75c587a10fbff20c04f2b23b

# Total reclaimed space: 32B
```


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)
> - [docker container prune | Docker Docs](https://docs.docker.com/reference/cli/docker/container/prune/)
