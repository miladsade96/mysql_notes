# Inserting, Updating and Deleting Data

## INSERT INTO:
The `INSERT INTO` statement in `SQL` is used to insert new rows into a table.

#### Adding a row to `customers` table without specifying the `column` names:
```mysql
Insert Into customers
values (
        DEFAULT,
        "John",
        "Smith",
        "1990-01-01",
        NULL,
        "Adress",
        "City",
        "CA",
        DEFAULT
    );
```

---

#### Adding a row to `customers` table with specifying the `column` names:
```mysql
Insert Into customers (first_name, last_name, address, city, state) 
values (
        'Milad',
        'Sadeghi',
        'Iran',
        'Tabriz',
        'EA'
    );
```

---

## Inserting Multiple Rows:

#### Adding multiple rows at one go to `shippers` table which has two columns (`shipper_id` and `name`) where `shipper_id` is automatic incremented so we don't need to specify it:
```mysql
INSERT INTO shippers (name)
VALUES ('Shipper1'),
       ('Shipper2'),
       ('Shipper3');
```

---

## Inserting Hierarchical Rows:

#### Adding a row to `orders` table which has three columns(`customer_id`, `order_date` and `status`) where
`customer_id` is a foreign key to `customers` table and inserting tow rows to `order_items` table which has four
columns(`order_id`, `product_id`, `quantity` and `unit_price`) where `order_id` is a foreign key to `orders` table and
`product_id` is a foreign key to `products` table:
```mysql
INSERT INTO orders (customer_id, order_date, status)
VALUES (1, '2019-01-02', 1);

INSERT INTO order_items
VALUES (LAST_INSERT_ID(), 1, 1, 2.95),
       (LAST_INSERT_ID(), 2, 1, 3.95);
```

---

## Creating a copy of a table:

#### Creating a copy table called `orders_archive` and inserting all rows of `orders` table into it:
```mysql
CREATE TABLE orders_archive AS 
SELECT * FROM orders;
```

---

#### Inserting all records of `orders` table where `order_date < 2019-01-01` and inserting them into `orders_archive` table:
```mysql
INSERT INTO orders_archive
SELECT *
FROM orders
WHERE order_date < "2019-01-01";
```

---
