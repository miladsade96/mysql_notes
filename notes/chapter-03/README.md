# Retrieving Data From Multiple Tables

## INNER JOIN:

#### Joining `orders_table` and `customers_table` based on `customer_id`:
```mysql
SELECT *
FROM orders_table
JOIN customers_table
ON orders_table.customer_id = customers_table.customer_id;

-- INNER is optional
```

---

#### Joining `orders_table` and `customers_table` based on `customer_id` and selecting only `order_id`, `first_name` and `last_name`:
```mysql
SELECT order_id, first_name, last_name
FROM orders_table
JOIN customers_table
ON orders_table.customer_id = customers_table.customer_id;
```

---


#### Joining `orders_table` and `customers_table` based on `customer_id` and selecting only `order_id`, `customer_id`, `first_name` and `last_name`:
```mysql
-- Since we have customer_id column in both tables, we need to specify its table

SELECT order_id, orders_table.customer_id, first_name, last_name
FROM orders_table
JOIN customers_table
ON orders_table.customer_id = customers_table.customer_id;
```

---

#### Simplifying query above by specifying aliases for tables:
```mysql
SELECT order_id, orders_table.customer_id, first_name, last_name
FROM orders_table o
JOIN customers_table c
ON o.customer_id = c.customer_id;
```
---
