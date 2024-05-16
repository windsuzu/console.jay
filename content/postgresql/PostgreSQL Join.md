---
draft: false
date: 2024-05-16 18:17
tags:
  - postgres
---


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

```sql
SELECT person.first_name, car.make, car.price
FROM person
JOIN car USING (car_uid)
```






> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
