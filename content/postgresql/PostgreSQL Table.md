---
draft: false
date: 2024-05-16 17:20
tags:
  - postgres
---

### Create a table

When creating a table, we can specify 3 slots for each column in the table. The column name, the data type, and any constraints:

```sql
CREATE TABLE table_name (
	column_name data_type optional_constraints
);
```

Take a look at the example below. We will create a table named `person`. It will have the following columns:

- `id`: an automatically incremented and generated id
- `first_name`: a non-null string with a maximum length of 50 characters
- `last_name`: a non-null string with a maximum length of 50 characters
- `gender`: a non-null string with a maximum length of 5 characters
- `date_of_birth`: a non-null datetime object
- `email`: a nullable string with a maximum length of 150 characters.

```sql
CREATE TABLE person (
	id BIGSERIAL NOT NULL PRIMARY KEY,
	first_name VARCHAR(50) NOT NULL,
	last_name VARCHAR(50) NOT NULL,
	gender VARCHAR(50) NOT NULL,
	date_of_birth DATE NOT NULL,
	email VARCHAR(150)
);
```

> [!tip] Other Data types
> To view all other data types, see [PostgreSQL: Documentation: Data Types](https://www.postgresql.org/docs/current/datatype.html)

### View tables

Use `\d` to display all relations (tables and sequences) in the current database.

```bash
\d

#              List of relations
# Schema |     Name      |   Type   |  Owner
#--------+---------------+----------+----------
# public | person        | table    | windsuzu
# public | person_id_seq | sequence | windsuzu
```

Use `\dt` to display all relations that are table type.

```bash
\dt

#          List of relations
#  Schema |  Name  | Type  |  Owner
# --------+--------+-------+----------
#  public | person | table | windsuzu
```


And use `\d table_name` to see the details of the specified table.

```bash
\d person

#                                        Table "public.person"
#     Column     |          Type          | Collation | Nullable |              Default
# ---------------+------------------------+-----------+----------+------------------------------------
#  id            | bigint                 |           | not null | nextval('person_id_seq'::regclass)
#  first_name    | character varying(50)  |           | not null |
#  last_name     | character varying(50)  |           | not null |
#  gender        | character varying(50)  |           | not null |
#  date_of_birth | date                   |           | not null |
#  email         | character varying(150) |           |          |
#
# Indexes:
#     "person_pkey" PRIMARY KEY, btree (id)
```

### Update a table

To update a table, use `ALTER`. For example, you can update the column name by using `ALTER TABLE` with `RENAME TO`:

```sql
ALTER TABLE table_name RENAME column_name TO column_new_name;

ALTER TABLE person RENAME id TO person_uid;
ALTER TABLE person RENAME gender TO sex;
```

Additionally, you can update the column type by using `ALTER TABLE` with `ALTER COLUMN` and `TYPE`:

```sql
ALTER TABLE table_name ALTER COLUMN column_name TYPE type_name;

ALTER TABLE person ALTER COLUMN email TYPE varchar(300);
ALTER TABLE person ALTER COLUMN age TYPE int;
```
### Remove a table

To remove a table, use `DROP` to do so.

```sql
DROP TABLE table_name;
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners - YouTube](https://www.youtube.com/watch?v=qw--VYLpxG4)
