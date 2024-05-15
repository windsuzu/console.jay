---
draft: false
date: 2024-05-15 16:44
tags:
  - postgres
---

### Create a new DB

```sql
CREATE DATABASE name_of_db;
```

> [!warning] 
> Remember to put a semicolon `;` at the end of the command.

### List all DBs

```sql
\l

#                               List of databases
#   Name    |  Owner   | Encoding | Collate |  Ctype  |   Access privileges
# -----------+----------+----------+---------+---------+--------------------
# postgres  | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
# template0 | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres ...
# template1 | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres ...
# test      | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
```
### Go to a DB

```sql
\c name_of_db

postgres=# \c test
# You are now connected to database "test" as user "windsuzu".
test=#
```

### Remove a DB

```sql
DROP DATABASE name_of_db;
```

> [!warning] 
> Remember to put a semicolon `;` at the end of the command.


> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners - YouTube](https://www.youtube.com/watch?v=qw--VYLpxG4)
