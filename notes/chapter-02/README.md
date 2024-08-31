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
