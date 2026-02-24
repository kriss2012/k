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
