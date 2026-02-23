# 📘 DBMS / PL-SQL Practical Programs (12–27)

---

# ✅ Practical 16
## Demonstrate GROUP BY and ORDER BY

```sql
CREATE TABLE employee (
    empno INT PRIMARY KEY,
    ename VARCHAR(30),
    deptno INT,
    salary NUMBER(10)
);

INSERT INTO employee VALUES (101,'Rahul',10,25000);
INSERT INTO employee VALUES (102,'Sneha',20,30000);
INSERT INTO employee VALUES (103,'Amit',10,28000);
INSERT INTO employee VALUES (104,'Priya',30,35000);

-- GROUP BY
SELECT deptno, AVG(salary) AS avg_salary
FROM employee
GROUP BY deptno;

-- ORDER BY
SELECT * FROM employee
ORDER BY salary DESC;
```

---

# ✅ Practical 17 & 18
## Create Department Table and Perform Operations

```sql
CREATE TABLE department (
    deptno INT PRIMARY KEY,
    deptname VARCHAR(30),
    location VARCHAR(30)
);

-- Add column designation
ALTER TABLE department
ADD designation VARCHAR(30);

-- Insert values
INSERT INTO department VALUES (1,'HR','Pune','Manager');
INSERT INTO department VALUES (2,'IT','Mumbai','Developer');
INSERT INTO department VALUES (9,'Sales','Delhi','Executive');

-- Group by deptno
SELECT deptno, COUNT(*) 
FROM department
GROUP BY deptno;

-- Update record where deptno = 9
UPDATE department
SET location = 'Nagpur'
WHERE deptno = 9;

-- Delete column data (example: delete designation column)
ALTER TABLE department
DROP COLUMN designation;
```

---

# ✅ Practical 19
## PL/SQL – Display Employee Details using Explicit Cursor

```sql
DECLARE
    CURSOR emp_cursor IS SELECT * FROM employee;
    emp_record employee%ROWTYPE;
BEGIN
    OPEN emp_cursor;
    LOOP
        FETCH emp_cursor INTO emp_record;
        EXIT WHEN emp_cursor%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE(emp_record.empno || ' ' || emp_record.ename);
    END LOOP;
    CLOSE emp_cursor;
END;
/
```

---

# ✅ Practical 20
## Retrieve Employee Details by Employee Number

```sql
DECLARE
    v_empno employee.empno%TYPE := &Enter_EmpNo;
    v_name employee.ename%TYPE;
    v_salary employee.salary%TYPE;
BEGIN
    SELECT ename, salary INTO v_name, v_salary
    FROM employee
    WHERE empno = v_empno;

    DBMS_OUTPUT.PUT_LINE('Name: ' || v_name);
    DBMS_OUTPUT.PUT_LINE('Salary: ' || v_salary);
END;
/
```

---

# ✅ Practical 21
## Update Salary of Employees Earning Less than Average

```sql
DECLARE
    CURSOR sal_cursor IS 
        SELECT empno, salary FROM employee
        WHERE salary < (SELECT AVG(salary) FROM employee);

BEGIN
    FOR rec IN sal_cursor LOOP
        UPDATE employee
        SET salary = salary + 2000
        WHERE empno = rec.empno;
    END LOOP;
END;
/
```

---

# ✅ Practical 22
## Trigger to Backup Salary Before Update

```sql
CREATE TABLE salary_backup (
    empno INT,
    old_salary NUMBER(10),
    updated_date DATE
);

CREATE OR REPLACE TRIGGER salary_trigger
BEFORE UPDATE ON employee
FOR EACH ROW
BEGIN
    INSERT INTO salary_backup
    VALUES (:OLD.empno, :OLD.salary, SYSDATE);
END;
/
```

---

# ✅ Practical 23
## Procedure to Count Students by Percentage Range

```sql
CREATE TABLE student_course (
    sid INT,
    course VARCHAR(30),
    percentage NUMBER(5)
);

CREATE OR REPLACE PROCEDURE grade_count(p_course VARCHAR)
IS
BEGIN
    SELECT COUNT(*) INTO :high
    FROM student_course
    WHERE percentage BETWEEN 70 AND 100
    AND course = p_course;
END;
/
```

---

# ✅ Practical 24
## Function to Add Two Numbers

```sql
CREATE OR REPLACE FUNCTION add_numbers(a NUMBER, b NUMBER)
RETURN NUMBER
IS
BEGIN
    RETURN a + b;
END;
/

-- Call function
SELECT add_numbers(10,20) FROM dual;
```

---

# ✅ Practical 25
## Function to Return Total Salary of Department

```sql
CREATE OR REPLACE FUNCTION total_salary(p_deptno NUMBER)
RETURN NUMBER
IS
    total NUMBER;
BEGIN
    SELECT SUM(salary) INTO total
    FROM employee
    WHERE deptno = p_deptno;

    RETURN total;
END;
/

-- Call function
SELECT total_salary(10) FROM dual;
```

---

# ✅ Practical 26
## User Defined and Built-in Exceptions

```sql
DECLARE
    v_salary NUMBER := 0;
    salary_exception EXCEPTION;
BEGIN
    IF v_salary <= 0 THEN
        RAISE salary_exception;
    END IF;
EXCEPTION
    WHEN salary_exception THEN
        DBMS_OUTPUT.PUT_LINE('Invalid Salary');
    WHEN ZERO_DIVIDE THEN
        DBMS_OUTPUT.PUT_LINE('Divide by Zero Error');
END;
/
```

---

# ✅ Practical 27
## Reverse a String using PL/SQL

```sql
DECLARE
    str VARCHAR2(50) := 'HELLO';
    rev VARCHAR2(50);
BEGIN
    FOR i IN REVERSE 1..LENGTH(str) LOOP
        rev := rev || SUBSTR(str,i,1);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed String: ' || rev);
END;
/
```
