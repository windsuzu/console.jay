---
draft: false
date: 2024-05-18 17:36
tags:
  - postgres
---

Other than [[PostgreSQL Primary Key and Foreign Key|primary and foreign keys]], we can define constraints on any column during table creation (CREATE TABLE) or table modification (ALTER TABLE). These constraints can be forcing uniqueness or custom conditions.

### NOT NULL

```sql
-- Define NOT NULL constraint when creating table
CREATE TABLE example (
    name VARCHAR(100) NOT NULL
);

-- Define NOT NULL constriant by modifying table
ALTER TABLE example ALTER COLUMN name SET NOT NULL;

-- Remove NOT NULL constraint by modifying table
ALTER TABLE example ALTER COLUMN name DROP NOT NULL;
```
### UNIQUE

```sql
-- Define UNIQUE constraint when creating table
CREATE TABLE example (
    email VARCHAR(150) UNIQUE
);

-- Define UNIQUE constraint by modifying table with named constraint
ALTER TABLE example ADD CONSTRAINT unique_email UNIQUE (email);
-- Define UNIQUE constraint by modifying table without naming constraint
ALTER TABLE example ADD UNIQUE (email);

-- Remove UNIQUE constraint by modifying table
ALTER TABLE example DROP CONSTRAINT unique_email;
```
### CHECK

```sql
-- Define CHECK constraint when creating table
CREATE TABLE example (
    age INT CHECK (age >= 18)
);

-- Define CHECK constraint by modifying table with named constraint
ALTER TABLE example ADD CONSTRAINT check_age CHECK (age >= 18);

-- Remove CHECK constraint by modifying table
ALTER TABLE example DROP CONSTRAINT check_age;
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
