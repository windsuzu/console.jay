---
draft: false
date: 2025-05-16 22:58
tags:
  - java
  - spring-boot
---

Dependency Injection is a specific and widely used implementation of the [[Inversion of control (IoC)]] principle. It focuses on how objects receive their dependencies (other objects they need to function). Instead of an object creating its own dependencies, these dependencies are "injected" into the object from an external source (the IoC container, e.g. Spring Container).

Spring Core heavily relies on Dependency Injection to manage the beans (objects) within its application context. Spring provides several ways to perform dependency injection:
1. [[Constructor Injection]]
2. [[Setter Injection]]
3. [[Field Injection (Not Recommend)]]

While all three methods are supported by Spring, **[[constructor injection]] is generally considered the preferred approach** for mandatory dependencies due to its benefits in terms of clarity, immutability, and testability. [[Setter injection]] can be used for optional dependencies. [[Field Injection (Not Recommend)]] should be used sparingly due to its drawbacks in terms of testability and explicit dependencies