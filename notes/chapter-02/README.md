# Retrieving Data From A Single Table

## SELECT:

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

---

## WHERE:

#### Selecting all customers with *points* greater than 3000:
```mysql
SELECT * FROM customers_table WHERE points > 3000;

-- Other operators: >   >=  <   <=  =   !=  <>
```

---

#### Selecting only customers that are located in virginia:
```mysql
SELECT * FROM customers_table WHERE state = "VA";
-- String "VA" is not case sensitive
```

---

#### Selecting all customers that are located outside of virginia:
```mysql
SELECT * from customers_table WHERE state != "VA";
-- != and <> are equivalent
```

---

#### Selecting only customers are born after january first 1990:
```mysql
SELECT *
FROM customers_table
WHERE birth_date > "1990-01-01";    -- Date default format in sql: yyyy-mm-dd
```
---

## AND, OR, NOT:

#### Selecting all customers that are born after january first 1990 and have points more than 1000:
```mysql
Select * From customers_table WHERE birth_date > "1990-01-01" AND points > 1000;

-- Both conditions should be true
```

---

#### Selecting all customers that are born after january first 1990 or have points more than 1000:
```mysql
Select * FROM customers_table WHERE birth_date > "1990-01-01" OR points > 1000;

-- At least one of the conditions should be true
```

---

#### Selecting all customers that are born either after 1990 or they have more than 1000 points and live in virginia:
```mysql
SELECT * from customers_table WHERE birth_date > "1990-01-01" OR points > 1000 AND state = "VA";

-- AND operator always evaluated before OR
```

---

#### Selecting all customers that are not born after january first 1990 or not have points more than 1000:
```mysql
Select * FROM customers_table WHERE NOT (birth_date > "1990-01-01" OR points > 1000);

-- Equivalent to below:

Select * FROM customers_table WHERE birth_date <= "1990-01-01" AND points <= 1000;
```

---

## IN:

#### Selecting all customers that are located in virginia or georgia or florida:
```mysql
SELECT * FROM customers_table WHERE state = "VA" OR state = "GA" OR state = "FL";

-- Equivalent to below using IN operator:

Select * FROM customers_table WHERE state IN ("VA", "GA", "FL");
```

---

#### Selecting all customers that are not located in virginia or georgia or florida:
```mysql
SELECT * FROM customers_table WHERE state NOT IN ("VA", "GA", "FL");
```

---

## BETWEEN:

#### Selecting all customers that have more than 1000 and less than 3000 points:
```mysql
SELECT * FROM customers_table where points BETWEEN 1000 AND 3000;

-- Range is inclusive ---> 1000 <= points <= 3000 
```

---

## LIKE:

#### Selecting only customers who's last name starts with `b`:
```mysql
SELECT * FROM customers_table WHERE last_name LIKE "b%";

-- % means any number of characters - case insensitive
```

---

#### Selecting only customers who's last name starts with `brush`:
```mysql
SELECT * FROM customers_table WHERE last_name LIKE "brush%";
```

---

#### Selecting all customers who have `b` somewhere in their last name:
```mysql
SELECT * FROM cusomers_table WHERE last_name LIKE "%b%";
```

---

#### Selecting only customers who's last name ends with `y`:
```mysql
SELECT * FROM customers_table WHERE last_name LIKE "%y";
```

---

#### Selecting only customers whose length of their last name is 6 characters and ends with `y`;
```mysql
SELECT * FROM customers_table WHERE last_name LIKE "_____y";

-- _ means a single character
```

---

#### Selecting only customers whose length of their last name is 6 characters and starts with `b` and ends with `y`;
```mysql
SELECT * FROM customers_table WHERE last_name LIKE "b____y";
```

---
