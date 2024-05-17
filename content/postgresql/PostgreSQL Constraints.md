---
draft: false
date: 2024-05-17 23:32
tags:
  - postgres
---

Other than [[PostgreSQL Primary Key and Foreign Key|primary and foreign keys]], we can define constraints on any column during table creation (CREATE TABLE) or table modification (ALTER TABLE). These constraints can be forcing uniqueness or custom conditions.

### NOT NULL

```sql
CREATE TABLE example (
    name VARCHAR(100) NOT NULL
);

ALTER TABLE example ALTER COLUMN name SET NOT NULL;

ALTER TABLE example ALTER COLUMN name DROP NOT NULL;
```
### UNIQUE

```sql
CREATE TABLE example (
    email VARCHAR(150) UNIQUE
);

ALTER TABLE example ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE example ADD UNIQUE (email);

ALTER TABLE example DROP CONSTRAINT unique_email;
```
### CHECK

```sql
CREATE TABLE example (
    age INT CHECK (age >= 18)
);

ALTER TABLE example ADD CONSTRAINT check_age CHECK (age >= 18);

ALTER TABLE example DROP CONSTRAINT check_age;
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
