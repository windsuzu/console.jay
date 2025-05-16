---
draft: false
date: 2025-05-16 23:27
tags:
  - java
  - spring-boot
---

The `@Value` annotation in Spring is used to inject values into fields, constructor parameters, or method parameters. These values can come from various sources, including:

- **Properties files:** Typically `application.properties` or `application.yml`.
- **Environment variables:** Operating system environment variables.
- **System properties:** Java system properties.
- **SpEL (Spring Expression Language):** For more complex value resolution.

## Common Use Cases and Examples

### 1. Injecting Values from Properties Files
Assume you have an `application.properties` file like this:
```
app.name=My Awesome Application
app.version=1.0.0
database.url=jdbc:postgresql://localhost:5432/mydb
database.username=admin
```
You can inject these values into your Spring beans like this:
```java
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component
public class AppConfig {

    @Value("${app.name}")
    private String applicationName;

    @Value("${app.version}")
    private String version;

    @Value("${database.url}")
    private String dbUrl;

    @Value("${database.username}")
    private String dbUser;
}
```
### 2. Injecting Environment Variables and System Properties
You can also access environment variables and system properties using `@Value`:
```java
@Component
public class SystemInfo {

    @Value("${JAVA_HOME}") // Accessing an environment variable
    private String javaHome;

    @Value("${user.dir}")   // Accessing a system property
    private String currentWorkingDirectory;
}
```
### 3. Using Default Values
Sometimes, a configuration property might not be defined. You can provide a default value using the following syntax:
```java
@Component
public class FeatureToggle {

    @Value("${feature.new-dashboard:false}") // Default to false
    private boolean newDashboardEnabled;

}
```
### 4. Injecting into Constructor Parameters
You can also use `@Value` to inject values into constructor parameters:
```java
@Service
public class NotificationService {

    private final String senderEmail;

    public NotificationService(@Value("${notification.sender.email}") String senderEmail) {
        this.senderEmail = senderEmail;
    }

    public void sendNotification(String recipient, String message) {
        System.out.println("Sending email from: " + senderEmail + " to: " + recipient + " with message: " + message);
    }
}
```
### 5. Injecting into Method Parameters
Less commonly used, but you can also inject values into method parameters:
```java
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

@Component
public class ReportGenerator {

    public void generateMonthlyReport(@Value("${report.month}") String month,
                                     @Value("${report.year}") int year) {
        System.out.println("Generating report for " + month + ", " + year);
    }
}
```