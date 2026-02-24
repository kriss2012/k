-

✅ 1) Basic Structure of ASP.NET Web Page

📄 Default.aspx

<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>

<!DOCTYPE html>
<html>
<head runat="server">
    <title>Basic ASP.NET Page</title>
</head>
<body>
    <form id="form1" runat="server">
        <div>
            <asp:Label ID="lblMessage" runat="server" Text="Hello ASP.NET"></asp:Label>
        </div>
    </form>
</body>
</html>

📄 Default.aspx.cs

using System;

public partial class _Default : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        lblMessage.Text = "Welcome to ASP.NET Web Forms";
    }
}


---

✅ 2) ASP.NET Controls Demo

📄 ControlsDemo.aspx

<%@ Page Language="C#" AutoEventWireup="true" CodeFile="ControlsDemo.aspx.cs" Inherits="ControlsDemo" %>

<!DOCTYPE html>
<html>
<body>
<form runat="server">
    Name:
    <asp:TextBox ID="txtName" runat="server"></asp:TextBox>
    <br /><br />

    <asp:Button ID="btnSubmit" runat="server" Text="Submit" OnClick="btnSubmit_Click" />
    <br /><br />

    <asp:Label ID="lblResult" runat="server"></asp:Label>
</form>
</body>
</html>

📄 ControlsDemo.aspx.cs

using System;

public partial class ControlsDemo : System.Web.UI.Page
{
    protected void btnSubmit_Click(object sender, EventArgs e)
    {
        lblResult.Text = "Hello " + txtName.Text;
    }
}


---

✅ 3) ViewState, Session & Application Demo

📄 StateDemo.aspx

<%@ Page Language="C#" AutoEventWireup="true" CodeFile="StateDemo.aspx.cs" Inherits="StateDemo" %>

<!DOCTYPE html>
<html>
<body>
<form runat="server">
    <asp:Button ID="btnViewState" runat="server" Text="ViewState" OnClick="btnViewState_Click" />
    <asp:Button ID="btnSession" runat="server" Text="Session" OnClick="btnSession_Click" />
    <asp:Button ID="btnApplication" runat="server" Text="Application" OnClick="btnApplication_Click" />
    <br /><br />
    <asp:Label ID="lblOutput" runat="server"></asp:Label>
</form>
</body>
</html>

📄 StateDemo.aspx.cs

using System;

public partial class StateDemo : System.Web.UI.Page
{
    protected void btnViewState_Click(object sender, EventArgs e)
    {
        ViewState["count"] = 1;
        lblOutput.Text = "ViewState value: " + ViewState["count"];
    }

    protected void btnSession_Click(object sender, EventArgs e)
    {
        Session["user"] = "Krishna";
        lblOutput.Text = "Session value: " + Session["user"];
    }

    protected void btnApplication_Click(object sender, EventArgs e)
    {
        Application["app"] = "BCA Project";
        lblOutput.Text = "Application value: " + Application["app"];
    }
}


---

✅ 4) Student Registration Form

📄 Registration.aspx

<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Registration.aspx.cs" Inherits="Registration" %>

<!DOCTYPE html>
<html>
<body>
<form runat="server">

Name:
<asp:TextBox ID="txtName" runat="server"></asp:TextBox>
<asp:RequiredFieldValidator ID="rfvName" runat="server"
    ControlToValidate="txtName"
    ErrorMessage="Name Required" ForeColor="Red"></asp:RequiredFieldValidator>
<br /><br />

Email:
<asp:TextBox ID="txtEmail" runat="server"></asp:TextBox>
<asp:RegularExpressionValidator ID="revEmail" runat="server"
    ControlToValidate="txtEmail"
    ValidationExpression="\w+@\w+\.\w+"
    ErrorMessage="Invalid Email" ForeColor="Red">
</asp:RegularExpressionValidator>
<br /><br />

<asp:Button ID="btnRegister" runat="server" Text="Register" OnClick="btnRegister_Click" />
<br /><br />

<asp:Label ID="lblMsg" runat="server"></asp:Label>

</form>
</body>
</html>

📄 Registration.aspx.cs

using System;

public partial class Registration : System.Web.UI.Page
{
    protected void btnRegister_Click(object sender, EventArgs e)
    {
        if (Page.IsValid)
        {
            lblMsg.Text = "Registration Successful!";
        }
    }
}


---

✅ 5) Calendar Control Demo

📄 CalendarDemo.aspx

<%@ Page Language="C#" AutoEventWireup="true" CodeFile="CalendarDemo.aspx.cs" Inherits="CalendarDemo" %>

<!DOCTYPE html>
<html>
<body>
<form runat="server">
    <asp:Calendar ID="Calendar1" runat="server" OnSelectionChanged="Calendar1_SelectionChanged"></asp:Calendar>
    <br />
    <asp:Label ID="lblDate" runat="server"></asp:Label>
</form>
</body>
</html>

📄 CalendarDemo.aspx.cs

using System;

public partial class CalendarDemo : System.Web.UI.Page
{
    protected void Calendar1_SelectionChanged(object sender, EventArgs e)
    {
        lblDate.Text = "Selected Date: " + Calendar1.SelectedDate.ToShortDateString();
    }
}


---

✅ 6) AdRotator Control Demo

📄 AdRotatorDemo.aspx

<%@ Page Language="C#" AutoEventWireup="true" CodeFile="AdRotatorDemo.aspx.cs" Inherits="AdRotatorDemo" %>

<!DOCTYPE html>
<html>
<body>
<form runat="server">
    <asp:AdRotator ID="AdRotator1" runat="server" AdvertisementFile="Ads.xml" />
</form>
</body>
</html>

📄 Ads.xml

<Advertisements>
  <Ad>
    <ImageUrl>image1.jpg</ImageUrl>
    <NavigateUrl>https://www.google.com</NavigateUrl>
    <AlternateText>Google</AlternateText>
  </Ad>
  <Ad>
    <ImageUrl>image2.jpg</ImageUrl>
    <NavigateUrl>https://www.microsoft.com</NavigateUrl>
    <AlternateText>Microsoft</AlternateText>
  </Ad>
</Advertisements>


---

If you want, I can now continue with:

✅ GridView with ADO.NET

✅ DropDownList Subject Selection

✅ Checkbox & RadioButton

✅ Cookies Program

✅ Master Page

✅ Server.Transfer & Response.Redirect

✅ Intrinsic Objects

✅ Windows Computer Name Program


Tell me which practical number you want next 👌INSERT INTO department VALUES (2, 'IT', 'Mumbai', 'Developer');
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


---�
