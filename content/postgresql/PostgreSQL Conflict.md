---
draft: false
date: 2024-05-18 22:17
tags:
  - postgres
---

When you insert or update a record in the table, the action may encounter a violation of primary key or unique constraints. You can use `ON CONFLICT` to specify the following action when the conflict occurs.

### ON CONFLICT DO NOTHING

The first thing you can do when a conflict occurs is to ignore it instead of throwing an error.

```sql
CREATE TABLE example (
    id SERIAL PRIMARY KEY,
    email VARCHAR(150) UNIQUE,
    name VARCHAR(100)
);

INSERT INTO example (email, name)
VALUES ('john@example.com', 'John Doe')
ON CONFLICT (email) DO NOTHING;
```

### ON CONFLICT DO UPDATE

On the other hand, you can update specific column




> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4) 
