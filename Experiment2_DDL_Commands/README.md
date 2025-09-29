<img width="1344" height="307" alt="image" src="https://github.com/user-attachments/assets/e5803954-d4ff-4212-a5f2-a944a961eb75" /><img width="1280" height="277" alt="image" src="https://github.com/user-attachments/assets/a4cf7e8f-c8f3-4b28-b409-772d77ad3a6b" /># Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT
For example:

Test	Result
pragma table_info('Departments');
cid    name             type        notnull     dflt_value  pk
-----  ---------------  ----------  ----------  ----------  ----------
0      DepartmentID     INTEGER     0                       0
1      DepartmentName   TEXT        0                       0


```sql
-- CREATE TABLE Departments (
    DepartmentID INTEGER,
    DepartmentName TEXT
);
```

**Output:**

<img width="1280" height="277" alt="image" src="https://github.com/user-attachments/assets/3f3b5471-2483-4498-92a5-b097c2eb173f" />

**Question 2**
---
-- Write an SQL command can to add a column named email of type TEXT to the customers table

 

For example:

Test	Result
pragma table_info('Customers');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           name        text        0                       0
2           email       TEXT        0                       0

```sql
--ALTER TABLE customers ADD COLUMN email TEXT;
```

**Output:**
<img width="1270" height="301" alt="image" src="https://github.com/user-attachments/assets/9edb08a6-eec1-4bfa-83b7-5b204423244d" />


**Question 3**
---
-- Insert a product with ProductID 104, Name Tablet, and Category Electronics into the Products table, where Price and Stock should use default values.

For example:

Test	Result
SELECT ProductID, Name, Category, Price, Stock 
FROM Products 
WHERE ProductID = 104;
ProductID   Name        Category     Price       Stock
----------  ----------  -----------  ----------  ----------
104         Tablet      Electronics  100         50


```sql
-- INSERT INTO Products (ProductID, Name, Category)
VALUES (104, 'Tablet', 'Electronics');
```

**Output:**

<img width="1272" height="285" alt="image" src="https://github.com/user-attachments/assets/03e42a6a-1f04-44c3-81a6-bbf54081a286" />

**Question 4**
---
-- In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021
For example:

Test	Result
SELECT * FROM Books;
ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021

```sql
-- INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES
  ('978-1234567890', 'Introduction to AI', 'John Doe', NULL, NULL),
  ('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', 2022),
  ('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', NULL, 2021);

```

**Output:**
<img width="1311" height="301" alt="image" src="https://github.com/user-attachments/assets/68e24ea3-dfed-46d7-9675-7177588c0f97" />


**Question 5**
---
-- Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 

 

 

For example:

Test	Result
pragma table_info('Companies');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          int         0                       0
1           first_name  varchar(50  0                       0
2           address     text        0                       0
3           email       varchar(50  0                       0
4           phone       varchar(10  0                       0
5           mobilenumb  number      0                       0
6           DOB         Date        0                       0


```sql
-- Paste your SQL code below for Question 5
```

**Output:**

![Output5](output.png)

**Question 6**
---
-- Write a SQL Query  to change the name of attribute "name" to "first_name"  and add mobilenumber as number ,DOB as Date in the table Companies. 

 

 

For example:

Test	Result
pragma table_info('Companies');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          int         0                       0
1           first_name  varchar(50  0                       0
2           address     text        0                       0
3           email       varchar(50  0                       0
4           phone       varchar(10  0                       0
5           mobilenumb  number      0                       0
6           DOB         Date        0                       0


```sql
-- -- Rename the column "name" to "first_name"
ALTER TABLE Companies RENAME COLUMN name TO first_name;

-- Add the new column "mobilenumber"
ALTER TABLE Companies ADD COLUMN mobilenumber number;

-- Add the new column "DOB"
ALTER TABLE Companies ADD COLUMN DOB Date;

```

**Output:**

<img width="1374" height="382" alt="image" src="https://github.com/user-attachments/assets/8a471a16-e05b-4b30-863d-db10bd82a1de" />

**Question 7**
---
--Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.
For example:

Test	Result
INSERT INTO Products (ProductID, ProductName, Price, StockQuantity) VALUES (1, 'Laptop', 999.99, 10);
select * from Products;
ProductID   ProductName  Price       StockQuantity
----------  -----------  ----------  -------------
1           Laptop       999.99      10


```sql
--CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL CHECK (Price > 0),
    StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1344" height="307" alt="image" src="https://github.com/user-attachments/assets/96f0142e-bdf8-44cf-a230-a06225c811f0" />

**Question 8**
---
--Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
For example:

Test	Result
INSERT INTO products (product_id, product_name, list_price) VALUES (2, 'Product B', 50.00);
SELECT * FROM products;
product_id  product_name  list_price  discount
----------  ------------  ----------  ----------
2           Product B     

```sql
-- CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    product_name TEXT NOT NULL,
    list_price DECIMAL(10, 2) NOT NULL,
    discount DECIMAL(10, 2) NOT NULL DEFAULT 0,
    CHECK (list_price >= discount AND discount >= 0 AND list_price >= 0)
);

```

**Output:**
<img width="1307" height="309" alt="image" src="https://github.com/user-attachments/assets/67879778-5556-415d-99e1-6769ab752124" />


**Question 9**
---
-- Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

For example:

Test	Result
select * from Books;
ISBN            Title           Author              Publisher      YearPublished
--------------  --------------  ------------------  -------------  -------------
978-1234567890  The Lost World  Arthur Conan Doyle  Vintage Books  1912
978-0987654321  Gone with the   Margaret Mitchell   Macmillan      1936
978-1122334455  Moby Dick       Herman Melville     Harper & Brot  1851

```sql
--
INSERT INTO Books
SELECT * FROM Out_of_print_books;


```

**Output:**
<img width="1311" height="317" alt="image" src="https://github.com/user-attachments/assets/c65180b2-20ec-420e-9b98-50235db2db74" />


**Question 10**
---
-- Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
For example:

Test	Result
INSERT INTO ProjectAssignments (AssignmentID, EmployeeID, ProjectID, AssignmentDate) VALUES (2, 99, 1, '2024-01-03');
Error: FOREIGN KEY constraint failed


```sql
-- CREATE TABLE ProjectAssignments (
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID),
    FOREIGN KEY (ProjectID) REFERENCES Projects(ProjectID)
);

```

**Output:**

<img width="1346" height="293" alt="image" src="https://github.com/user-attachments/assets/b7c2699d-efb7-40e1-bd9f-6a4a21004521" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
