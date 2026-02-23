Here is your complete content converted into a single Markdown (.md) file format, properly structured and ready to submit.

You can copy this directly into a file named:

oracle_practical_17_to_24.md


---

# Oracle SQL / PL-SQL Practical (17–24)

Clean, Runnable, Exam-Ready Code

---

## ✅ 17 & 18. Create Department Table + Operations

### a) Create Table

```sql
CREATE TABLE department (
    deptno INT PRIMARY KEY,
    deptname VARCHAR2(30),
    location VARCHAR2(30)
);


---

Add Column designation

ALTER TABLE department
ADD designation VARCHAR2(30);


---

b) Insert Values

INSERT INTO department VALUES (1, 'HR', 'Pune', 'Manager');
INSERT INTO department VALUES (2, 'IT', 'Mumbai', 'Developer');
INSERT INTO department VALUES (9, 'Finance', 'Delhi', 'Analyst');

COMMIT;


---

c) List Records Grouped by deptno

SELECT deptno, COUNT(*) 
FROM department
GROUP BY deptno
ORDER BY deptno;


---

d) Update Record Where deptno = 9

UPDATE department
SET location = 'Bangalore'
WHERE deptno = 9;

COMMIT;


---

e) Delete Column (designation)

ALTER TABLE department
DROP COLUMN designation;


---

✅ 19. PL/SQL – Display Employee Details Using Explicit Cursor

DECLARE
    CURSOR emp_cursor IS
        SELECT empno, ename, salary FROM employee;

    v_empno employee.empno%TYPE;
    v_ename employee.ename%TYPE;
    v_salary employee.salary%TYPE;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_empno, v_ename, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        DBMS_OUTPUT.PUT_LINE('Emp No: ' || v_empno ||
                             ' Name: ' || v_ename ||
                             ' Salary: ' || v_salary);
    END LOOP;

    CLOSE emp_cursor;
END;
/


---

✅ 20. Retrieve Employee Details Based on Input

DECLARE
    v_empno employee.empno%TYPE := &Enter_EmpNo;
    v_name employee.ename%TYPE;
    v_date employee.hiredate%TYPE;
    v_desig employee.designation%TYPE;
BEGIN
    SELECT ename, hiredate, designation
    INTO v_name, v_date, v_desig
    FROM employee
    WHERE empno = v_empno;

    DBMS_OUTPUT.PUT_LINE('Name: ' || v_name);
    DBMS_OUTPUT.PUT_LINE('Join Date: ' || v_date);
    DBMS_OUTPUT.PUT_LINE('Designation: ' || v_desig);

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Employee not found');
END;
/


---

✅ 21. Update Salary (Less than Average) Using Cursor

DECLARE
    CURSOR emp_cursor IS
        SELECT empno, salary FROM employee
        WHERE salary < (SELECT AVG(salary) FROM employee);

BEGIN
    FOR emp_rec IN emp_cursor LOOP
        UPDATE employee
        SET salary = salary + 1000
        WHERE empno = emp_rec.empno;
    END LOOP;

    COMMIT;
END;
/


---

✅ 22. Trigger – Backup Salary Before Update

CREATE TABLE salary_backup AS
SELECT * FROM employee WHERE 1=2;

CREATE OR REPLACE TRIGGER trg_salary_update
BEFORE UPDATE OF salary ON employee
FOR EACH ROW
BEGIN
    INSERT INTO salary_backup
    VALUES (:OLD.empno, :OLD.ename, :OLD.salary, :OLD.hiredate, :OLD.designation);
END;
/


---

✅ 23. Procedure – Count Students by Percentage Range

CREATE OR REPLACE PROCEDURE student_range_count(p_course VARCHAR2)
IS
    v_100_70 NUMBER;
    v_69_60 NUMBER;
    v_59_50 NUMBER;
    v_below49 NUMBER;
BEGIN
    SELECT COUNT(*) INTO v_100_70
    FROM student_course
    WHERE course = p_course AND marks BETWEEN 70 AND 100;

    SELECT COUNT(*) INTO v_69_60
    FROM student_course
    WHERE course = p_course AND marks BETWEEN 60 AND 69;

    SELECT COUNT(*) INTO v_59_50
    FROM student_course
    WHERE course = p_course AND marks BETWEEN 50 AND 59;

    SELECT COUNT(*) INTO v_below49
    FROM student_course
    WHERE course = p_course AND marks < 49;

    DBMS_OUTPUT.PUT_LINE('70-100: ' || v_100_70);
    DBMS_OUTPUT.PUT_LINE('60-69: ' || v_69_60);
    DBMS_OUTPUT.PUT_LINE('50-59: ' || v_59_50);
    DBMS_OUTPUT.PUT_LINE('Below 49: ' || v_below49);
END;
/


---

✅ 24. Function – Addition of Two Numbers

CREATE OR REPLACE FUNCTION add_numbers(a NUMBER, b NUMBER)
RETURN NUMBER
IS
BEGIN
    RETURN a + b;
END;
/

Call Function

DECLARE
    result NUMBER;
BEGIN
    result := add_numbers(10, 20);
    DBMS_OUTPUT.PUT_LINE('Sum = ' || result);
END;
/


---

✔ End of Practical 17–24

---

If you want, I can now:

- ✅ Format it with a professional college cover page  
- ✅ Convert it into PDF format  
- ✅ Add Practical 25–27 also  
- ✅ Add proper comments for viva explanation  

Tell me what you need 👍
