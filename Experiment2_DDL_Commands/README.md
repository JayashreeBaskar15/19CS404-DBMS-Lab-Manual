# Experiment 2: DDL Commands

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
-- Create a table named Products with the following constraints:
ProductID as INTEGER should be the primary key.
ProductName as TEXT should be unique and not NULL.
Price as REAL should be greater than 0.
StockQuantity as INTEGER should be non-negative.

```sql
-- CREATE TABLE Products(ProductID INTEGER PRIMARY KEY,ProductName TEXT UNIQUE NOT NULL, Price REAL,StockQuantity Integer,CHECK ((Price)>0),CHECK((StockQuantity)>0));
```

**Output:**

![image](https://github.com/user-attachments/assets/fabb29ed-dde8-4d72-b3f8-7384ee0805a6)


**Question 2**
---
-- Create a table named Products with the following columns:

ProductID as INTEGER
ProductName as TEXT
Price as REAL
Stock as INTEGER

```sql
-- create table Products(ProductID INTEGER,ProductName TEXT,Price REAL, Stock INTEGER);
```

**Output:**

![image](https://github.com/user-attachments/assets/216b9d76-6d35-4dd4-802b-a048eeafde4e)


**Question 3**
---
-- Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.

```sql
-- create table Department(DepartmentID INTEGER PRIMARY KEY,DepartmentName TEXT UNIQUE NOT NULL,Location TEXT);
```

**Output:**

![image](https://github.com/user-attachments/assets/0f6b95d1-cefe-47bf-81d6-13e6b5965b6e)


**Question 4**
---
-- Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300

```sqlinsert into Products (Name,Category,Price,Stock)values('Smartphone','Electronics',800,150),('Headphones','Accessories',200,300);Paste your SQL code below for Question 4
```

**Output:**

![image](https://github.com/user-attachments/assets/d8c570c3-5dd2-4fde-96f1-b7f596476749)


**Question 5**
---
-- Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.

```sql
-- insert into Customers(CustomerID,Name,Address)values(304,'Peter Parker','Spider St');
```

**Output:**

![image](https://github.com/user-attachments/assets/0e4026fe-665f-40a7-86a6-868a390bfd9d)


**Question 6**
---
-- Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700         COM5

```sql
--CREATE TABLE item(item_id TEXT PRIMARY KEY,item_desc TEXT NOT NULL,rate INTEGER NOT NULL,icom_id TEXT CHECK(length(icom_id)=4),FOREIGN KEY (icom_id)references company(com_id) ON UPDATE CASCADE ON DELETE CASCADE);
```

**Output:**
![image](https://github.com/user-attachments/assets/f973ee98-ba90-47ad-82ef-76089f3ab225)


**Question 7**
---
-- Write a SQL query to add a column named Date_of_birth as Date in the Student_details table.

```sql
-- alter table Student_details add Date_of_birth Date;
```

**Output:**

![image](https://github.com/user-attachments/assets/7ac70e65-ef45-4677-b40a-0e033fad0b38)


**Question 8**
---
-- Write a SQL query to Add a new column named "discount" with the data type DECIMAL(5,2) to the "customer" table.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

For example:

Test	Result
pragma table_info('customer');
cid         name         type                               notnull     dflt_value  pk
----------  -----------  ---------------------------------  ----------  ----------  ----------
0           customer_id  integer primarykey auto increment  0                       0
1           cust_name    varchar2(30)                       0                       0
2           city         varchar(30)                        0                       0
3           grade        number                             0                       0
4           salesman_id  number                             0                       0
5           discount     DECIMAL(5,2)                       0                       0


```sql
-- alter table customer add discount DECIMAL(5,2);
```

**Output:**

![image](https://github.com/user-attachments/assets/b74d4eec-f60a-4792-9af4-ddf5bf5db749)


**Question 9**
---
-- Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.

```sql
-- CREATE TABLE Employees(EmployeeID primary key,FirstName not null,LastName not null, Email unique,Salary ,DepartmentID int,foreign key(DepartmentID)references Departments,check((Salary)>0));
```

**Output:**

![image](https://github.com/user-attachments/assets/55657d55-13d1-4f76-b48d-a60a09a30095)


**Question 10**
---
-- Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

For example:

Test	Result
select * from Products;
ProductID   ProductName     Price       Stock
----------  --------------  ----------  ----------
101         Old Smartphone  199.99      0
102         Vintage Laptop  399.99      10
103         Classic Tablet  149.99      5


```sql
-- insert into Products(ProductID,ProductName,Price,Stock)select ProductID, ProductName, Price, Stock from Discontinued_products;
```

**Output:**

![image](https://github.com/user-attachments/assets/c0ca742c-9eff-45ae-8217-07f45d1bc670)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
