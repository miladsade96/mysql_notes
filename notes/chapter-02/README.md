# Retrieving Data From A Single Table

#### Selecting a database to query:
```mysql
USE database_Name;
```

---

#### Selecting all columns from a table:
```mysql
SELECT * FROM customers_table;
```

---

#### Filtering data using *WHERE* clause:
```mysql
SELECT * FROM customers_table WHERE customer_id = 1;
```

---

#### Sorting data based on a specific column:
```mysql
SELECT * FROM customers_table ORDER BY first_name;
```

---

#### Commenting out queries using --:
```mysql
-- SELECT * FROM customers_table;
```

---

#### Selecting specific columns to get from a table:
```mysql
SELECT first_name, last_name, points FROM customers_table;
```

---

#### Executing an arithmetic expression based on the column of the table:
```mysql
--- Order of math operators matter
SELECT first_name, last_name, points, points * 10 + 100 FROM customers_table;
```

---

#### Specifying an alias to arithmetic expression:
```mysql
SELECT 
    first_name,
    last_name,
    points,
    points * 10 + 100 AS discount_factor
FROM customers_table;
--- Alias name should be sourounded by quotes in case there is a space between
```

---

#### Selecting a unique list of values in the column:
```mysql
SELECT DISTINCT state FROM customers_table;
```