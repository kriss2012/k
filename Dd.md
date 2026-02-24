# 📘 ASP.NET Web Forms Practical Journal
Name: ____________________  
Class: BCA  
Subject: ASP.NET  
College: ____________________  

---

# ✅ Practical 1: Basic ASP.NET Page

## Default.aspx
```aspx
<%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>

<html>
<body>
<form runat="server">
    <asp:Label ID="lblMsg" runat="server"></asp:Label>
</form>
</body>
</html>
```

## Default.aspx.cs
```csharp
using System;

public partial class _Default : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        lblMsg.Text = "Welcome to ASP.NET";
    }
}
```

---

# ✅ Practical 2: ASP.NET Controls

```aspx
Enter Name:
<asp:TextBox ID="txtName" runat="server"></asp:TextBox>
<asp:Button ID="btn" runat="server" Text="Submit" OnClick="btn_Click" />
<asp:Label ID="lbl" runat="server"></asp:Label>
```

```csharp
protected void btn_Click(object sender, EventArgs e)
{
    lbl.Text = "Hello " + txtName.Text;
}
```

---

# ✅ Practical 3: ViewState, Session, Application

```csharp
protected void btnView_Click(object sender, EventArgs e)
{
    ViewState["msg"] = "ViewState Example";
    lbl.Text = ViewState["msg"].ToString();
}

protected void btnSession_Click(object sender, EventArgs e)
{
    Session["msg"] = "Session Example";
    lbl.Text = Session["msg"].ToString();
}

protected void btnApp_Click(object sender, EventArgs e)
{
    Application["msg"] = "Application Example";
    lbl.Text = Application["msg"].ToString();
}
```

---

# ✅ Practical 4: Validation Control

```aspx
Name:
<asp:TextBox ID="txtName" runat="server"></asp:TextBox>

<asp:RequiredFieldValidator 
    ID="rfv" 
    runat="server"
    ControlToValidate="txtName"
    ErrorMessage="Name Required"
    ForeColor="Red">
</asp:RequiredFieldValidator>
```

---

# ✅ Practical 5: DropDownList

```aspx
<asp:DropDownList ID="ddl" runat="server">
    <asp:ListItem>Math</asp:ListItem>
    <asp:ListItem>Science</asp:ListItem>
</asp:DropDownList>

<asp:Button ID="btn" runat="server" Text="Show" OnClick="btn_Click" />
<asp:Label ID="lbl" runat="server"></asp:Label>
```

```csharp
protected void btn_Click(object sender, EventArgs e)
{
    lbl.Text = ddl.SelectedItem.Text;
}
```

---

# ✅ Practical 6: CheckBox & RadioButton

```aspx
<asp:CheckBox ID="chk" runat="server" Text="Cricket" />
<br />

<asp:RadioButton ID="rb1" runat="server" Text="Male" GroupName="g" />
<asp:RadioButton ID="rb2" runat="server" Text="Female" GroupName="g" />

<br />
<asp:Button ID="btn" runat="server" Text="Submit" OnClick="btn_Click" />
<asp:Label ID="lbl" runat="server"></asp:Label>
```

```csharp
protected void btn_Click(object sender, EventArgs e)
{
    string result = "";

    if (chk.Checked)
        result += "Cricket ";

    if (rb1.Checked)
        result += "Male";

    if (rb2.Checked)
        result += "Female";

    lbl.Text = result;
}
```

---

# ✅ Practical 7: Cookies

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    Response.Cookies["User"].Value = "BCA Student";
    lbl.Text = Request.Cookies["User"].Value;
}
```

---

# ✅ Practical 8: Master Page

## Site.master
```aspx
<%@ Master Language="C#" %>

<html>
<body>
<h2>Master Page Header</h2>
<asp:ContentPlaceHolder ID="ContentPlaceHolder1" runat="server" />
</body>
</html>
```

## Home.aspx
```aspx
<%@ Page MasterPageFile="~/Site.master" %>

<asp:Content ContentPlaceHolderID="ContentPlaceHolder1" runat="server">
    Master Page Working
</asp:Content>
```

---

# ✅ Practical 9: Calendar Control

```aspx
<asp:Calendar ID="cal" runat="server" OnSelectionChanged="cal_SelectionChanged" />
<asp:Label ID="lbl" runat="server"></asp:Label>
```

```csharp
protected void cal_SelectionChanged(object sender, EventArgs e)
{
    lbl.Text = cal.SelectedDate.ToShortDateString();
}
```

---

# ✅ Practical 10: AdRotator

```aspx
<asp:AdRotator ID="AdRotator1" runat="server" AdvertisementFile="Ads.xml" />
```

---

# ✅ Practical 11: Server.Transfer & Response.Redirect

```csharp
protected void btnTransfer_Click(object sender, EventArgs e)
{
    Server.Transfer("Page2.aspx");
}

protected void btnRedirect_Click(object sender, EventArgs e)
{
    Response.Redirect("Page2.aspx");
}
```

---

# ✅ Practical 12: Intrinsic Objects

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    Response.Write("Server Name: " + Request.ServerVariables["SERVER_NAME"]);
    Response.Write("<br/>User IP: " + Request.UserHostAddress);
}
```

---

# ✅ Practical 13: Display Computer Name

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    Response.Write("Computer Name: " + Environment.MachineName);
}
```

---

# ✅ Practical 14: GridView with ADO.NET

## GridView.aspx
```aspx
<asp:GridView ID="GridView1" runat="server"></asp:GridView>
```

## GridView.aspx.cs
```csharp
using System;
using System.Data;
using System.Data.SqlClient;

protected void Page_Load(object sender, EventArgs e)
{
    SqlConnection con = new SqlConnection(
        "Data Source=.;Initial Catalog=TestDB;Integrated Security=True");

    SqlDataAdapter da = new SqlDataAdapter(
        "SELECT * FROM Students", con);

    DataTable dt = new DataTable();
    da.Fill(dt);

    GridView1.DataSource = dt;
    GridView1.DataBind();
}
```

---

# 🎓 End of Practical Journal
