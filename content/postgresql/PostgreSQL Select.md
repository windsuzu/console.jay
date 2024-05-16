---
draft: false
date: 2024-05-16 14:48
tags:
  - postgres
---

Use `ORDER BY` to sort the result by one or more columns. By default `ORDER BY` uses ascending order (`ASC`), you can change it to descending order by specifying `DESC`.

```sql
SELECT * FROM person ORDER BY date_of_birth ASC;
SELECT * FROM person ORDER BY date_of_birth DESC;
SELECT * FROM person ORDER BY gender DESC, date_of_birth ASC;
```

Use `DISTINCT` to list all distinct values in a column or a combination of columns.

```sql
SELECT DISTINCT gender FROM person;
SELECT DISTINCT gender, last_name FROM person;
```

Use `WHERE` with or without the following keywords or operators to select rows with conditions. 

- Use `AND`, `OR` to find union or intersection of conditions
- Use comparison operators like `>`, `<`, `>=`, `<=`, `=`, `<>` 
- Use `IN` to quickly select the matching ones in a pool
- Use `BETWEEN AND` to select values between a range
- Use `LIKE` to find values with a certain pattern (Both `%` and `_` denote placeholder)
- Use `ILIKE` to get the effect of `LIKE` but without the case sensitivity
- Use `IS NULL` to find values that are null.

```sql
SELECT * FROM person WHERE gender = 'Agender';
SELECT * FROM person WHERE gender = 'Male' AND date_of_birth > '2024-01-01';
SELECT * FROM person WHERE gender = 'Male' OR gender = 'Female';
SELECT * FROM person WHERE gender IN ('Male', 'Female', 'Agender');
SELECT * FROM person WHERE id BETWEEN 50 AND 55;
SELECT * FROM person WHERE last_name LIKE '%han';
SELECT * FROM person WHERE last_name ILIKE '____lan';
SELECT * FROM person WHERE email IS NULL;
```

Use `LIMIT` to show a certain number of rows. Then use `OFFSET` to skip the first N rows. 

```sql
SELECT * FROM person LIMIT 5 OFFSET 10;
```

Use `GROUP BY` to group rows with the same column value into summary rows. `GROUP BY` is often used with aggregate functions, such as `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`. In addition, you can use `GROUP BY HAVING` to add conditions.

```sql
SELECT gender, COUNT(*) FROM person GROUP BY gender;
SELECT gender, COUNT(*) FROM person GROUP BY gender HAVING COUNT(*) > 15;
SELECT gender, AVG(age) FROM person GROUP BY gender;
SELECT gender, MIN(age) FROM person GROUP BY gender;
SELECT gender, MAX(age) FROM person GROUP BY gender;
```

Use `AS` to assign aliases to columns that appear in the result.

```sql
SELECT date_of_birth AS birthday FROM person;
```

Use `COALESCE` as a useful tool for handling NULL values.

```sql
SELECT COALESCE(email, 'Not provided') FROM person;
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners - YouTube](https://www.youtube.com/watch?v=qw--VYLpxG4)
> - [PostgreSQL: Documentation: 9.5: Aggregate Functions](https://www.postgresql.org/docs/9.5/functions-aggregate.html)
