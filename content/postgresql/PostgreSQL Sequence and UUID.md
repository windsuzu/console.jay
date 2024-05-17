---
draft: false
date: 2024-05-17 23:37
tags:
  - postgres
---

### BIGSERIAL

The `BIGSERIAL` type assigns the column an auto-incrementing id starting at 1. If you want to restart the id number from a specific number, you can use `ALTER SEQUENCE` as the following statement.

```sql
ALTER SEQUENCE person_id_seq RESTART WITH 1;
```

### UUID







> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
> - [Universally unique identifier - Wikipedia](https://en.wikipedia.org/wiki/Universally_unique_identifier)
