---
draft: false
date: 2025-05-16 22:57
tags:
  - java
  - spring-boot
---

You can also directly inject dependencies into fields using `@Autowired`. However, this approach is generally discouraged for a few reasons (it can make testing harder and can lead to circular dependencies that are harder to detect).

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class ReportService {

    @Autowired
    private DataFetcher dataFetcher;

    public String generateReport() {
        List<String> data = dataFetcher.fetchData();
        return "Report generated with " + data.size() + " items.";
    }
}

@Component
public class DataFetcher {
    public List<String> fetchData() {
        return List.of("Data 1", "Data 2", "Data 3");
    }
}
```

Here, Spring directly injects an instance of `DataFetcher` into the `dataFetcher` field of `ReportService`.