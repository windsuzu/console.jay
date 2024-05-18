---
draft: false
date: 2024-05-18 17:37
tags:
  - postgres
---

Use the following SQL command to insert a new row into the table.

```sql
INSERT INTO table_name (
	col1_name,
	col2_name,
) VALUES (col1_val, col2_val);
```

For example:

```sql
INSERT INTO person (first_name, last_name, email, gender, date_of_birth) VALUES ('Alvan', 'Fearnall', null, 'Male', '2024-05-12');
```

### Import from a SQL file

Suppose you have a `.sql` file with 1000 insert statements, you can use `\i file_relative_path` to execute all the commands in the file.

```sql
-- /mnt/c/Users/winds/Desktop/person.sql

insert into person (first_name, last_name, email, gender, date_of_birth) values ('Alvan', 'Fearnall', null, 'Male', '2024-05-12');
insert into person (first_name, last_name, email, gender, date_of_birth) values ('Herbie', 'Tollit', null, 'Male', '2023-12-18');
insert into person (first_name, last_name, email, gender, date_of_birth) values ('Currey', 'Kira', null, 'Male', '2023-08-02');
...
```

You need to first get the relative path of the SQL file, then paste it into `psql`.

```bash
pwd
# /mnt/c/Users/winds/Desktop

\i /mnt/c/Users/winds/Desktop/person.sql
# INSERT 0 1
# INSERT 0 1
# INSERT 0 1
# ...

SELECT * FROM person
#   id  | first_name  |      last_name       |   gender    | date_of_birth |               email
# ------+-------------+----------------------+-------------+---------------+------------------------------------
#    1 | Alvan       | Fearnall             | Male        | 2024-05-12    |
#    2 | Herbie      | Tollit               | Male        | 2023-12-18    |
#    3 | Currey      | Kira                 | Male        | 2023-08-02    |
#    4 | Elysha      | Dowling              | Female      | 2023-07-27    | edowling3@yelp.com
#    5 | Chip        | Corsham              | Agender     | 2023-08-12    | ccorsham4@virginia.edu
#    6 | Emili       | Barnby               | Female      | 2024-02-09    | ebarnby5@netscape.com
# ...
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners - YouTube](https://www.youtube.com/watch?v=qw--VYLpxG4)
> - [Mockaroo - Random Data Generator and API Mocking Tool](https://www.mockaroo.com/)
