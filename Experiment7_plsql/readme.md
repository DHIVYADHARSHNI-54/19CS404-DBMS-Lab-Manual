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
## program
```
DECLARE
    num1 NUMBER := 80;
    num2 NUMBER := 45;
BEGIN
    IF num1 > num2 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num1);
    ELSIF num2 > num1 THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || num2);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Both numbers are equal: ' || num1);
    END IF;
END;
```

## output

![image](https://github.com/user-attachments/assets/3d66098c-a9a6-4db6-8685-f1deda5ba61e)


## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

## program
```
DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
```

## output

![image](https://github.com/user-attachments/assets/0e1791a6-2080-4730-8d15-b490d151f1cc)


## 3. Write a PL/SQL program to generate Fibonacci series

## program
```
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 1;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');

    WHILE i <= n LOOP
        IF i = 1 THEN
            DBMS_OUTPUT.PUT_LINE(a);
        ELSIF i = 2 THEN
            DBMS_OUTPUT.PUT_LINE(b);
        ELSE
            c := a + b;
            DBMS_OUTPUT.PUT_LINE(c);
            a := b;
            b := c;
        END IF;
        i := i + 1;
    END LOOP;
END;

```
## output

![image](https://github.com/user-attachments/assets/1bd9b5ca-7dea-48d1-bf93-1512dec1538d)



## 4. Write a PL/SQL Program to display the number in Reverse Order

## program
```
DECLARE
    n NUMBER := 1535;
    reversed NUMBER := 0;
    digit NUMBER;
    original NUMBER := n;
BEGIN
    WHILE n > 0 LOOP
        digit := MOD(n, 10);         -- Extract the last digit
        reversed := reversed * 10 + digit;  -- Build the reversed number
        n := TRUNC(n / 10);          -- Remove the last digit
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Original number is: ' || original);
    DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || reversed);
END;
```

## output

![image](https://github.com/user-attachments/assets/07c05cf6-5e3f-4114-af37-558c681227bb)

## 5. Write a PL/SQL program to find the largest of three numbers

## program
```
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
BEGIN
    IF a >= b AND a >= c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || a);
    ELSIF b >= a AND b >= c THEN
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || b);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || c);
    END IF;
END;
```

## output

![image](https://github.com/user-attachments/assets/13da7714-704a-4cfd-a94e-b10bc3696bd0)

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
