# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
--For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
For example:

Test	Result
SELECT*FROM Products WHERE supplier_id = 10;
product_id  product_name      category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ----------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Detergent Powder  Snacks      60          80          20           40          10
7           Surf Excel Deter  Snacks      85          100         10           40          10
8           Detergent Ariel   Items       85          100         10           40          10
product_id  product_name      category    cost_price  sell_price  reorder_lvl  quantity    supplier_id
----------  ----------------  ----------  ----------  ----------  -----------  ----------  -----------
6           Detergent Powder  Snacks      60          81          20           40          10
7           Surf Excel Deter  Snacks      85          114         10           40          10
8           Detergent Ariel   Items       85          114         10           40          10

```sql
-- update PRODUCTS
set sell_price=round(cost_price*1.35)
where (sell_price-cost_price)/sell_price*100<30;
```

**Output:**

![Output1](output.png)

**Question 2**
---
-- Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:

Test	Result
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL,COMMISSION_PCT FROM EMPLOYEES 
WHERE DEPARTMENT_ID=110 LIMIT 1;
EMPLOYEE_ID  FIRST_NAME  EMAIL          COMMISSION_PCT
-----------  ----------  -------------  --------------
205          Shelley     not available  0.55


```sql
-- update Employees
set EMAIL="not available",COMMISSION_PCT=0.55
where department_id=110;
```

**Output:**

![image](https://github.com/user-attachments/assets/a2b9e0ae-519a-4d6c-8d3c-78e39743fe20)


**Question 3**
---
-- Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id

```sql
-- update Employees
set first_name="John"
where department_id=80 and commission_pct<=0.25;
```

**Output:**

![image](https://github.com/user-attachments/assets/22c07e74-a842-4497-a498-51b6d3e6e1c8)


**Question 4**
---
-- Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT           

```sql
--update Products
set sell_price=sell_price*1.15
where quantity<50 and supplier_id=10;
```

**Output:**

![image](https://github.com/user-attachments/assets/0e16e9b2-49fe-498c-904b-d97d3d3d5f94)


**Question 5**
---
-- Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability

```sql
-- update products
set product_name="Grapefruit"
where product_id=4 ;
```

**Output:**

![image](https://github.com/user-attachments/assets/1947aae9-cb44-4254-9f44-935f9275d3d0)


**Question 6**
---
-- Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB

```sql
-- delete from customer
where length(CUST_NAME)=6;
```

**Output:**

![image](https://github.com/user-attachments/assets/31616b6e-4005-4531-8494-b8e2c2782fd5)


**Question 7**
---
-- Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
-- delete from Surgeries
where surgery_id=3;
```

**Output:**

![image](https://github.com/user-attachments/assets/b5c39471-5118-407b-9d0d-baebb59b4a3f)


**Question 8**
---
--  Write a query to fetch details of all employees excluding the employees with first names, “Sanjay” and “Sonia” from the EmployeeInfo table
Result
EmpID       EmpFname    EmpLname    Department  Project     Address     DOB         Gender
----------  ----------  ----------  ----------  ----------  ----------  ----------  ----------
2           Ananya      Mishra      Admin       P2          Delhi(DEL)  1968-05-02  F
3           Rohan       Diwan       Account     P3          Mumbai(BOM  1980-01-01  M
5           Ankit       Kapoor      Admin       P2          Delhi(DEL)  1994-07-03  M


```sql
-- select * from EmployeeInfo where EmpFname NOT IN("Sanjay","Sonia");
```

**Output:**

![image](https://github.com/user-attachments/assets/6f501f3f-045d-468e-8f09-661af282a7c1)


**Question 9**
---
-- Write a SQL query to retrieve the details of all customers whose ID belongs to any of the values 3007, 3008 or 3009. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
-- select * from customer
where customer_id IN(3007,3008,3009);
```

**Output:**

![image](https://github.com/user-attachments/assets/a515fc5f-e679-4258-bd81-02c29648bc24)


**Question 10**
---
-- Write a SQL query to retrieve all orders where the purchase amount is between 500 and 4000 but exclude orders with purchase amounts of 948.50 and 1983.43. The query should return the columns: ord_no, purch_amt, ord_date, customer_id, and salesman_id.

Table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005

```sql
--select * from orders 
where purch_amt between 500 and 4000 
and purch_amt NOT IN (948.50,1983.43);
```

**Output:**

![image](https://github.com/user-attachments/assets/09c65aac-5739-461e-9703-9cbaf2d04815)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
