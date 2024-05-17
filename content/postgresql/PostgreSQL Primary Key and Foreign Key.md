---
draft: false
date: 2024-05-17 23:14
tags:
  - postgres
---

### Primary Key

We can assign a primary key to a single column or to a combination of columns, either when creating a table (`CREATE TABLE`) or when altering a table (`ALTER TABLE`).

```sql
CREATE TABLE person (
	id BIGSERIAL PRIMARY KEY,
	name VARCHAR(100)
);

CREATE TABLE person (
	id BIGSERIAL,
	name VARCHAR(100),
	PRIMARY KEY (id, name)
);

ALTER TABLE person ADD PRIMARY KEY (id);
ALTER TABLE person ADD PRIMARY KEY (id, name);
```

To remove a primary key from a table, you can use the `ALTER TABLE` statement to do it. Find the name of the primary key by using `\d table_name` before removing it.

```sql
ALTER TABLE person DROP CONSTRAINT person_pkey;
```
### Foreign Key

We can create a relationship between two tables by using a foreign key from the child table to create a link to the primary key of the parent table. Creating a relationship between two tables can enable us to perform some useful commands, like `JOIN`, to [[PostgreSQL Join|join two tables]].

```sql
CREATE TABLE person (
	id BIGSERIAL PRIMARY KEY,
	name VARCHAR(100)
);

CREATE TABLE car (
	id BIGSERIAL PRIMARY KEY,
	person_id BIGINT,
	FOREIGN KEY (person_id) REFERENCES person (id)	
);
```

To remove a foreign key from a table, you can also use the `ALTER TABLE` statement do to it.

```sql
ALTER TABLE car DROP CONSTRAINT car_person_id_fkey;
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
