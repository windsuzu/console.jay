---
draft: false
date: 2024-05-18 17:23
tags:
  - postgres
---

### BIGSERIAL

The `BIGSERIAL` type assigns the column an auto-incrementing id starting at 1. If you want to restart the id number from a specific number, you can use `ALTER SEQUENCE` as the following statement.

```sql
ALTER SEQUENCE person_id_seq RESTART WITH 1;
```

### UUID

[UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) stands for Universally Unique Identifier and is a data type designed to store unique identifiers. A UUID is globally unique, which means it is unique even across different systems.

```sql
CREATE TABLE example (
    id UUID PRIMARY KEY,
    name VARCHAR(100)
);
```

Before inserting a record with a UUID, you have to install a UUID generator from `uuid-ossp`. You can install it with the following SQL command.

```sql
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";
```

Now when you insert a record, you can call `uuid_generate_v4()` or [other versions can be found in the documentation](https://www.postgresql.org/docs/current/uuid-ossp.html) for your `id` field.

```sql
-- Inserting a single row with a generated UUID
INSERT INTO example (id, name) VALUES (uuid_generate_v4(), 'John');

-- Inserting multiple rows with generated UUIDs
INSERT INTO example (id, name) 
VALUES 
    (uuid_generate_v4(), 'Alice'),
    (uuid_generate_v4(), 'Bob');
```


> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
> - [Universally unique identifier - Wikipedia](https://en.wikipedia.org/wiki/Universally_unique_identifier)
