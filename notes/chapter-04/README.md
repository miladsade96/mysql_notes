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
