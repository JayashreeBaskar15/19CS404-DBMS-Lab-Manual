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
-- What is the total number of appointments scheduled for each day?

Table: Appointments

name                 type
-------------------  ----------
AppointmentID        INTEGER
PatientID            INTEGER
DoctorID             INTEGER
AppointmentDateTime  DATETIME
Purpose              TEXT
Status               TEXT

```sql
-- select DATE(AppointmentDateTime) as AppointmentDate,count(*) as TotalAppointments
from Appointments group by AppointmentDate order by AppointmentDate;
```

**Output:**

![image](https://github.com/user-attachments/assets/8326f6b3-fed5-4e05-bb3f-83cce62a7e7a)


**Question 2**
---
-- What is the total number of medications prescribed for each patient?

Sample tablePrescriptions Table



```sql
-- select PatientID,count(*)as TotalMedications
from Prescriptions group by PatientID;
```

**Output:**

![image](https://github.com/user-attachments/assets/15d4d7f0-76eb-4ebf-a19b-2fff0112fcb4)


**Question 3**
---
-- Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

```sql
--select min(purch_amt) as "MINIMUM"
from orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/65336be5-fb6a-4438-b4b8-8905aa8696c6)

**Question 4**
---
-- Write a SQL query to find the shortest email address in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
-- select name,email,length(email) as min_email_length
from customer order by length(email) asc limit 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/7d75cdef-9e22-4a5b-baa5-a837f5a4646e)


**Question 5**
---
-- Write a SQL query to find the youngest employee in the company?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
--select name as Employee_Name,age as Age
from employee where AGE=(select MIN(Age) from employee)limit 1;
```

**Output:**

![image](https://github.com/user-attachments/assets/a6dcad6b-a437-44a4-80ee-1a0f045cedac)


**Question 6**
---
-- Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

```sql
-- select count(distinct salesman_id)as "COUNT"
from orders;
```

**Output:**

![image](https://github.com/user-attachments/assets/c668fef2-3822-4ed7-89ba-824e70b5d2a0)


**Question 7**
---
--Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.

```sql
-- select age,sum(income) as "SUM(income)"
from employee group by age having Sum(income)>1000000;

**Output:**

![image](https://github.com/user-attachments/assets/78959eed-0385-420c-b25d-609a204b0c12)


**Question 8**
---
-- Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.

```sql
-- select city, avg(income) as "AVG(income)"
from employee group by city having AVG(income)>500000;

**Output:**

![image](https://github.com/user-attachments/assets/4dd724a3-ca7a-42fe-9163-aac849058e7f)


**Question 9**
---
-- Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.
```sql
-- select age,income as "MAX(income)"
from employee group by age having MAX(income)>2000000;
```

**Output:**

![image](https://github.com/user-attachments/assets/a8473727-6b18-49eb-be57-128719f257e0)


**Question 10**
---
-- How many prescriptions were written by each doctor?
```sql
-- select DoctorID,COUNT(*) as TotalPrescriptions
from Prescriptions
group by DoctorID;
```

**Output:**

![image](https://github.com/user-attachments/assets/245053c9-8df5-444d-b60d-40e43388ba8f)



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
