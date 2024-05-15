---
draft: false
date: 2024-05-15 19:32
tags:
  - postgres
---

Use `ORDER BY` to sort the result by one or more columns.

```sql
# default is ASC
SELECT * FROM person ORDER BY date_of_birth ASC;
SELECT * FROM person ORDER BY date_of_birth DESC;
SELECT * FROM person ORDER BY gender DESC, date_of_birth ASC;
```

Use `DISTINCT` to list all distinct values in a column or a combination of columns.

```sql
SELECT DISTINCT gender FROM person
SELECT DISTINCT gender, last_name FROM person
```

Use `WHERE` and 


: `AND` `OR` `COMPARISON OPERATORS` `>` `<` `>=` `<=` `=` `<>` `IN` `BETWEEN AND` `LIKE` `ILIKE`


`LIMIT`:


`OFFSET`:


`GROUP BY`:


`GROUP BY HAVING`:


AGGREGATE FUNCTIONS


`AS`:


`COALESCE`:



> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners - YouTube](https://www.youtube.com/watch?v=qw--VYLpxG4)
> - [PostgreSQL: Documentation: 9.5: Aggregate Functions](https://www.postgresql.org/docs/9.5/functions-aggregate.html)
