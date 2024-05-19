---
draft: false
date: 2024-05-19 16:20
tags:
  - postgres
---

You can join rows from two or more tables based on foreign keys between them. Let's explore different `JOIN` methods by creating two tables `customers` and `orders`.

```sql
CREATE TABLE customers (
    customer_id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    product VARCHAR(100),
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers (customer_id)
);
```

Now let's add some data to both tables.

```sql
INSERT INTO customers (name) VALUES
('Alice'),
('Bob'),
('Charlie');

--  customer_id |  name
-- -------------+---------
--            1 | Alice
--            2 | Bob
--            3 | Charlie

INSERT INTO orders (customer_id, product) VALUES
(1, 'Laptop'),
(2, 'Smartphone'),
(2, 'Tablet'),
(2, 'Monitor');

--  order_id | customer_id |  product
-- ----------+-------------+------------
--         1 |           1 | Laptop
--         2 |           2 | Smartphone
--         3 |           2 | Tablet
--         4 |           2 | Monitor
```
### Inner Join

The `INNER JOIN` returns only rows that have matching values in both tables. In the example, the result does not return *Charlie* because there is no order of *Charlie* in the `orders` table.

```sql
SELECT customers.name, orders.product
FROM customers
INNER JOIN orders ON customers.customer_id = orders.customer_id;

--  name  |  product
-- -------+------------
--  Alice | Laptop
--  Bob   | Smartphone
--  Bob   | Tablet
--  Bob   | Monitor
```
### Left Join

The `LEFT JOIN` returns all rows from the left table regardless of whether there is a match in the right table.

```sql
SELECT customers.name, orders.product
FROM customers
LEFT JOIN orders ON customers.customer_id = orders.customer_id;

--   name   |  product
-- ---------+------------
--  Alice   | Laptop
--  Bob     | Smartphone
--  Bob     | Tablet
--  Bob     | Monitor
--  Charlie |
```

### Right Join

The `RIGHT JOIN` returns all rows from the right table regardless of whether there is a match in the left table.

```sql
SELECT customers.name, orders.product
FROM customers
RIGHT JOIN orders ON customers.customer_id = orders.customer_id;

--  name  |  product
-- -------+------------
--  Alice | Laptop
--  Bob   | Smartphone
--  Bob   | Tablet
--  Bob   | Monitor
```

### Full Join

The `FULL JOIN` returns all rows from both the left and the right tables, regardless of whether there is a match between two tables.

```sql
SELECT customers.name, orders.product
FROM customers
FULL JOIN orders ON customers.customer_id = orders.customer_id;

--   name   |  product
-- ---------+------------
--  Alice   | Laptop
--  Bob     | Smartphone
--  Bob     | Tablet
--  Bob     | Monitor
--  Charlie |
```
### Cross Join

The `CROSS JOIN` returns the Cartesian product of two tables.

```sql
SELECT customers.name, orders.product
FROM customers
CROSS JOIN orders;

--   name   |  product
-- ---------+------------
--  Alice   | Laptop
--  Alice   | Smartphone
--  Alice   | Tablet
--  Alice   | Monitor
--  Bob     | Laptop
--  Bob     | Smartphone
--  Bob     | Tablet
--  Bob     | Monitor
--  Charlie | Laptop
--  Charlie | Smartphone
--  Charlie | Tablet
--  Charlie | Monitor
```

> [!info] References
> - [Learn PostgreSQL Tutorial - Full Course for Beginners (youtube.com)](https://www.youtube.com/watch?v=qw--VYLpxG4)
