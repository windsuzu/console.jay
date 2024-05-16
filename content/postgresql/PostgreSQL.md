---
draft: false
date: 2024-05-16 15:51
tags:
  - postgres
---

- [[Install PostgreSQL on WSL 2 (Ubuntu)]]
- [[Connect PostgreSQL on WSL 2 (Ubuntu)]] 
- [[PostgreSQL Databases]]
- [[PostgreSQL Tables]]
- [[PostgreSQL Insert and Import]]
- [[PostgreSQL Select]]

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)

```sql
ALTER TABLE person ADD UNIQUE (email);
ALTER TABLE person ADD CONSTRAINT unique_email UNIQUE (email);
```

```sql
ALTER TABLE person DROP CONSTRAINT person_pkey;
```

```sql
ALTER TABLE person ADD PRIMARY KEY (id);
```

```sql
ALTER TABLE person ADD CONSTRAINT gender_contraint CHECK (gender = 'Female' OR gender = 'Male');
```

```sql
UPDATE person SET first_name = 'Omar', last_name = 'Montana' WHERE id = 2011;
```

```sql
DELETE FROM person;

```

```sql
DELETE FROM person WHERE id = 1; 
```

```sql
ON CONFLICT (id) DO NOTHING;
ON CONFLICT (id) DO UPDATE SET email = EXCLUDED.email;
ON CONFLICT (id) DO UPDATE SET email = EXCLUDED.email, gender = EXCLUDED.gender;
```

```sql
CREATE TABLE car (
	id BIGSERIAL NOT NULL PRIMARY KEY,
	make VARCHAR(100) NOT NULL,
	model VARCHAR(100) NOT NULL,
	price NUMERIC(19,2) NOT NULL
);

CREATE TABLE person (
	id BIGSERIAL NOT NULL PRIMARY KEY,
	first_name VARCHAR(50) NOT NULL,
	last_name VARCHAR(50) NOT NULL,
	gender VARCHAR(50) NOT NULL,
	date_of_birth DATE NOT NULL,
	email VARCHAR(150),
	car_id BIGINT REFERENCE car(id),
	UNIQUE(car_id)
);
```

```sql
UPDATE person SET car_id = 2 WHERE id = 1;
```

### JOIN

```sql
JOIN car ON person.car_id = car.id;
```

```sql
SELECT person.first_name, car.make, car.price
FROM person
JOIN car ON person.car_id = car.id
```

```sql
SELECT person.first_name, car.make, car.price
FROM person
LEFT JOIN car ON person.car_id = car.id
```

### ALTER SEQUENCE

```sql
ALTER SEQUENCE person_id_seq RESTART WITH 0;
```

