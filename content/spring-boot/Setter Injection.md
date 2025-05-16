---
draft: false
date: 2025-05-16 22:56
tags:
  - java
  - spring-boot
---

Besides [[Constructor Injection]], another way to inject dependencies is through setter methods. While less common than constructor injection, it's still supported.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class EmailService {

    private MessageSender messageSender;

    @Autowired
    public void setMessageSender(MessageSender messageSender) {
        this.messageSender = messageSender;
    }

    public void sendEmail(String to, String subject, String body) {
        messageSender.sendMessage(to, subject, body);
    }
}

@Component
public class MessageSender {
    public void sendMessage(String to, String subject, String body) {
        System.out.println("Sending message to: " + to);
        // ... actual sending logic
    }
}
```

Here, Spring uses the `@Autowired` annotation on the `setMessageSender` method to inject an instance of `MessageSender` into `EmailService`.