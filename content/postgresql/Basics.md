---
draft: false
date: 2024-05-14 23:13
tags:
  - tbd
---

Install PostgreSQL and run it in WSL 2:
[Install and use Postgres in WSL - DEV Community](https://dev.to/sfpear/install-and-use-postgres-in-wsl-423d)

Create a new database:

```sql
CREATE DATABASE your_db_name;
```

List all databases and go to a specific database:

```bash
# list all database
\l
#                               List of databases
#   Name    |  Owner   | Encoding | Collate |  Ctype  |   Access privileges
# -----------+----------+----------+---------+---------+--------------------
# postgres  | postgres | UTF8     | C.UTF-8 | C.UTF-8 |
# template0 | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres ...
# template1 | postgres | UTF8     | C.UTF-8 | C.UTF-8 | =c/postgres ...
# test      | postgres | UTF8     | C.UTF-8 | C.UTF-8 |

# go to the test database
\c test
```



> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
