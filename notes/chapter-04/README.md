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
