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

## Joining Across Databases:

#### Joining `order_items` table from `sql_store` database with `products` table from `sql_inventory` database based on `product_id`:
```mysql
SELECT *
FROM sql_store.order_items oi
JOIN sql_inventory.products p
ON oi.product_id = p.product_id;
```

---

## Self Joins:

#### Joining `employees` table from `sql_hr` database with itself in order to get the `employee_id`, `employee first name` and `manager first name`:
```mysql
SELECT e.employee_id, e.first_name AS "Employee FirstName", m.first_name AS "Manager FirstName"
FROM sql_hr.employees e
JOIN sql_hr.employees m
ON e.reports_to = m.employee_id;
```

---

## Joining Multiple Tables:

#### Joining `orders`, `customers` and `orders_statuses` tables based on `customer_id` and `order_status_id` columns. And then selecting only `order_id`, `order_date`, `first_name`, `last_name` and `status_name` columns:
```mysql
USE sql_store;

SELECT o.order_id, o.order_date, c.first_name, c.last_name, os.name AS status
FROM orders o
JOIN customers c
ON o.customer_id = c.customer_id
JOIN order_statuses os
ON o.status = os.order_status_id;
```

---

## Compound Join Condition:

#### Joining two `order_items` and `order_item_notes` tables based on two `order_id` and `product_id` columns:
```mysql
SELECT *
FROM order_items oi
JOIN order_item_notes oin
ON oi.order_id = oin.order_Id
AND oi.product_id = oin.product_id;
```

---

## Implicit Join Syntax:

#### Rewriting query below:
```mysql
SELECT *
FROM orders_table o 
JOIN customers_table c 
ON o.customer_id = c.customer_id;
```
Using implicit join syntax:
```mysql
SELECT *
FROM orders_table o, customers_table c 
WHERE o.customer_id = c.customer_id;

-- This is a bad practice, use always explicit join syntax
```

---

## OUTER JOIN:

#### Joining `customers` and `orders` tables based on `customer_id` and selecting only `customer_id`, `first_name` and `order_id` columns and finally sort the result based on `customer_id` colum:
```mysql
SELECT *
FROM customers_table c 
JOIN orders_table o 
ON o.customer_id = c.customer_id
ORDER BY c.customer_id;
```
And Extend the query above to display the customers who do not have order using outer join:
```mysql
SELECT *
FROM customers_table c 
LEFT JOIN orders_table o 
ON o.customer_id = c.customer_id
ORDER BY c.customer_id;

-- All customers regardles of having an order or not
```

---

## OUTER JOIN Between Multiple Tables:

#### Joining `customers` and `orders` tables based on `customer_id` and display all customers even those who does not have `order` and then joining `customers` and `shippers` tables based on `shipper_id` and display all `orders` even those who does not have `shipper` and finally selecting `customer_id`, `first_name`, `order_id` and `shipper name` columns and order them based on `customer_id` to display as result:
```mysql
SELECT *
FROM customers c 
LEFT JOIN orders o 
ON c.customer_id = o.customer_id
LEFT JOIN shippers sh
ON o.shipper_id = sh.shipper_id
ORDER BY c.customer_id;
```

---

## Self Outer Join

#### Selecting all employees whether they have a manager or not. This query will return the manager row itself as result because the manager is also an employee in the organization:
```mysql
Select 
    e.employee_id,
    e.first_name,
    m.first_name AS manager
FROM employees e 
LEFT JOIN employees m
ON e.reports_to = m.employee_id;
```

---
