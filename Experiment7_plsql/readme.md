# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80

**PL/SQL CODE:**
DECLARE
    num1 NUMBER;
    num2 NUMBER;
    greatest NUMBER;
BEGIN
    num1 := 50;  
    num2 := 80;  
    IF num1 > num2 THEN
        greatest := num1;
    ELSE
        greatest := num2;
    END IF;
    DBMS_OUTPUT.PUT_LINE('Greatest number is: ' || greatest);
END;

**OUTPUT:**
![image](https://github.com/user-attachments/assets/c2e71e71-563b-4762-a32c-77e743192a24)

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

**PL/SQL CODE:**
DECLARE
    n NUMBER := 10;  -- You can change this value as needed
    sum NUMBER := 0;
    i NUMBER := 1;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;

**OUTPUT:**
![image](https://github.com/user-attachments/assets/c244cde9-de39-4ed1-a655-83098f6876f9)


## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

**PL/SQL CODE:**
VARIABLE n NUMBER
ACCEPT n NUMBER PROMPT 'n = '
DECLARE
   a NUMBER := 0;
   b NUMBER := 1;
   c NUMBER;
   i NUMBER := 3; 
BEGIN
   IF :n <= 0 THEN
      DBMS_OUTPUT.PUT_LINE(' ');
   ELSIF :n = 1 THEN
      DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: 0');
   ELSIF :n = 2 THEN
      DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: 0, 1');
   ELSE
      DBMS_OUTPUT.PUT('Fibonacci sequence: 0, 1');
      WHILE i <= :n LOOP
         c := a + b;
         DBMS_OUTPUT.PUT(', ' || c);
         a := b;
         b := c;
         i := i + 1;
      END LOOP;
      DBMS_OUTPUT.NEW_LINE;
   END IF;
END;
/

**OUTPUT:**
![image](https://github.com/user-attachments/assets/92324c97-867d-49a8-ae92-884b6f8dbda4)

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

**PL/SQL CODE:**
DECLARE
   n NUMBER := 1535;         
   original NUMBER := n;     
   reversed NUMBER := 0;
   digit NUMBER;
BEGIN
   WHILE n > 0 LOOP
      digit := MOD(n, 10);              
      reversed := (reversed * 10) + digit;  
      n := TRUNC(n / 10);               
    END LOOP;

   DBMS_OUTPUT.PUT_LINE('n = ' || original);
   DBMS_OUTPUT.PUT_LINE('Reversed number is ' || reversed);
END;
/

**OUTPUT:**
![image](https://github.com/user-attachments/assets/6ec295d2-b459-4282-a217-d76ac42b54d0)

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

**PL/SQL CODE:**
DECLARE
    num1 NUMBER;
    num2 NUMBER;
    num3 NUMBER;
    greatest NUMBER;
BEGIN
    num1 := 50;  
    num2 := 90; 
    num3 :=120; 
    IF (num1 > num2) and (num1>num3) THEN
        greatest := num1;
    ELSIF (num2>num1) and (num2>num3) THEN
        greatest := num2;
    ELSE
        greatest :=num3;
    END IF;
    DBMS_OUTPUT.PUT_LINE('Largest of three number is: ' || greatest);
END;

**OUTPUT:**
![image](https://github.com/user-attachments/assets/b2cccb2a-db2c-48d9-bfe1-b63b1882de78)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
