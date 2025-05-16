---
draft: false
date: 2025-05-16 22:55
tags:
  - java
  - spring-boot
---

This is a very common and recommended way to handle dependencies. Spring will automatically resolve and inject the required dependencies through the constructor of your class.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class UserService {

    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public User getUserById(Long id) {
        return userRepository.findById(id).orElse(null);
    }
}

@Service
public class AnotherService {

    private final UserService userService;

    @Autowired
    public AnotherService(UserService userService) {
        this.userService = userService;
    }

    public void processUser(Long id) {
        User user = userService.getUserById(id);
        // ... do something with the user
    }
}

@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    // ... your repository methods
}

@Entity
public class User {
    @Id
    private Long id;
    private String name;
    // ... other properties and getters/setters
}
```

In this example:

- `UserService` depends on `UserRepository`. Instead of `UserService` creating an instance of `UserRepository`, Spring creates an instance of `UserRepository` (because of the `@Repository` annotation) and passes it into the constructor of `UserService` (due to the `@Autowired` annotation on the constructor).
- Similarly, `AnotherService` depends on `UserService`, and Spring manages this dependency as well.