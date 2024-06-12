---
draft: false
date: 2024-06-12 16:00
tags:
  - docker
---

Docker is an ecosystem comprising the Docker Client (CLI), Docker Daemon (Server), Docker Hub, Docker Images, and Docker Compose, all working together to achieve ==containerization==. Containerization involves encapsulating the necessary steps, dependencies, and configurations for setting up software or executing an application into a single [[Docker Container|container]] instance.

![[how-docker-works.png]]

When you run `docker run hello-world` for the first time, the Docker Client asks the Docker Server to run this command. The Docker Server first looks for the `hello-world` image in the **image cache** on your machine. If there's no such image on your machine, it then pulls it from the Docker Hub over the Internet and caches it. Finally, the Docker server takes the image, loads it into memory, creates a [[Docker Container|container]] from it, and runs the program inside it.


> [!info] References
> - [Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide)