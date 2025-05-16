---
draft: false
date: 2025-05-16 23:13
tags:
  - java
  - spring-boot
---

Imagine you have a bunch of classes in your Spring Boot application that you want Spring to manage as beans. Instead of manually defining each bean in an XML configuration file (which was common in older Spring versions), component scanning automates this process. Spring will "scan" specific packages in your project, look for classes annotated with certain stereotypes (like `@Component`, `@Service`, `@Repository`, `@Controller`, `@RestController`), and automatically register them as beans in the Application Context.

When your Spring Boot application starts, the Spring framework initiates the component scanning process. Here's a simplified view of what happens:

1. **Configuration:** You typically tell Spring which packages to scan. This is often done implicitly through the location of your main application class (the one annotated with `@SpringBootApplication`).
2. **Scanning:** Spring traverses the specified packages and their sub-packages.
3. **Annotation Detection:** During the scan, Spring looks for classes annotated with specific stereotype annotations:
	- `@Component`: A generic stereotype for any Spring-managed component.
	- `@Service`: A specialization of `@Component` indicating a service-layer component.
	- `@Repository`: A specialization of `@Component` indicating a data access component (often used with JPA repositories).
	- `@Controller`: A specialization of `@Component` indicating a controller in a web application (handling incoming requests).
	- `@RestController`: A convenience annotation that combines `@Controller` and `@ResponseBody`, often used for building RESTful APIs.
4. **Bean Registration:** When Spring finds a class annotated with one of these stereotypes, it registers that class as a bean in the Application Context. The bean's name is usually the lowercase version of the class name (e.g., `UserService` becomes `userService`). You can also explicitly specify a name using the `value` attribute of the annotation (e.g., `@Service("myUserService")`).

You might encounter situations where you need more control over which packages are scanned. You can customize the packages to be scanned using the `@ComponentScan` annotation. You can place this annotation on your main application class or any `@Configuration` class. Here are a few ways to use `@ComponentScan`:

1. Scanning specific packages
```java
@SpringBootApplication
@ComponentScan({"com.example.myapp.service", "com.example.myapp.repository"})
public class MySpringBootApplication {
	...
}
```

2. canning based on base packages
```java
@SpringBootApplication
@ComponentScan(basePackageClasses = {UserService.class, UserRepository.class})
public class MySpringBootApplication {
	...
}
```

```java
@SpringBootApplication
@ComponentScan(basePackages = "com.example.myapp")
public class MySpringBootApplication {
	...
}
```

3. Using filters to include or exclude specific components
```java
@SpringBootApplication
@ComponentScan( 
	basePackages = "com.example.myapp", 
	excludeFilters = @ComponentScan.Filter(type = FilterType.ANNOTATION, classes = Deprecated.class)
)
public class MySpringBootApplication {
	...
}
```