# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
--What is the most common diagnosis among patients?

Sample table:MedicalRecords Table



For example:

Result
Diagnosis              DiagnosisCount
---------------------  --------------
Childhood vaccination  3

```sql
-- SELECT 
    Diagnosis,
    COUNT(*) AS DiagnosisCount
FROM MedicalRecords
GROUP BY Diagnosis
ORDER BY DiagnosisCount DESC
LIMIT 1;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0b2134a1-396a-4111-a16f-bac336161447" />

**Question 2**
---
-- How many medical records were created in each month?

Sample table:MedicalRecords Table



For example:

Result
Month       TotalRecords
----------  ------------
2023-12     2
2024-01     6
2024-02     2


```sql
-- SELECT 
    strftime('%Y-%m', date) AS Month,
    COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY strftime('%Y-%m', date)
ORDER BY Month;
```

**Output:**

![Uploading image.png…]()

**Question 3**
---
-- How many medical records does each doctor have?

Sample table:MedicalRecords Table



For example:

Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3

```sql
-- SELECT 
    DoctorID,
    COUNT(*) AS TotalRecords
FROM 
    MedicalRecords
GROUP BY 
    DoctorID
ORDER BY 
    DoctorID;
```

**Output:**

<img width="534" height="507" alt="image" src="https://github.com/user-attachments/assets/e6c57bde-4f7d-4d83-9354-6bf9c8b13e96" />

**Question 4**
---
-- Write a SQL query to find the customer with longest name?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
name          length
------------  ----------
Preeti Patel  12


```sql
-- SELECT 
    name,
    LENGTH(name) AS length
FROM 
    customer
ORDER BY 
    LENGTH(name) DESC
LIMIT 1;
```

**Output:**

<img width="635" height="260" alt="image" src="https://github.com/user-attachments/assets/457d331a-358e-4572-87de-6cb105da0a93" />


**Question 5**
---
--Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

Result
employees_in_california
-----------------------
2

```sql
-- SELECT 
    COUNT(*) AS employees_in_california
FROM 
    employee
WHERE 
    city = 'California';
```

**Output:**

<img width="538" height="258" alt="image" src="https://github.com/user-attachments/assets/4328493f-457a-4268-bd71-590a5acfb561" />

**Question 6**
---
--Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer



 

For example:

Result
COUNT
----------
1


```sql
-- SELECT 
    COUNT(*) AS COUNT
FROM 
    customer
WHERE 
    city = 'Noida';
```

**Output:**

<img width="430" height="267" alt="image" src="https://github.com/user-attachments/assets/55569bec-103a-46a5-be61-b9bfbe2ee7b7" />

**Question 7**
---
-- Write a SQL query to count the number of customers. Return number of customers.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

 

For example:

Result
COUNT
----------
8


```sql
-- SELECT 
    COUNT(*) AS COUNT
FROM 
    customer;
```

**Output:**

<img width="316" height="240" alt="image" src="https://github.com/user-attachments/assets/5604e868-9c0f-4573-9449-d7c75d5cf616" />

**Question 8**
---
-- Write the SQL query that accomplishes the grouping of data by age intervals using the expression (age/5)5, calculates the minimum age for each group, and excludes groups where the minimum age is not less than 25.

Sample table: customer1



For example:

Result
age_group   MIN(age)
----------  ----------
20          22

```sql
-- SELECT 
    (age/5)*5 AS age_group,
    MIN(age) AS "MIN(age)"
FROM 
    customer1
GROUP BY 
    (age/5)*5
HAVING 
    MIN(age) < 25
ORDER BY
    age_group;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/aa379ae9-de9c-4249-bcce-943c9d52aa53" />

**Question 9**
---
-- Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

Sample table: products



For example:

Result
category_id  Total_Cost
-----------  ----------
2            63


```sql
-- SELECT 
    category_id,
    SUM(price) AS Total_Cost
FROM 
    products
GROUP BY 
    category_id
HAVING 
    SUM(price) > 50
ORDER BY
    category_id;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/7e4920a2-891f-49c0-918e-4b3088d91792" />

**Question 10**
---
--Write the SQL query that achieves the grouping of data by age, calculates the minimum income for each age group, and includes only those age groups where the minimum income is less than 400,000.

Sample table: employee



For example:

Result
age         MIN(income)
----------  -----------
32          200000
40          350000


```sql
-- SELECT 
    age,
    MIN(income) AS "MIN(income)"
FROM 
    employee
GROUP BY 
    age
HAVING 
    MIN(income) < 400000
ORDER BY
    age;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3641f4c1-87a2-486e-9292-0fa39e5b2a02" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
