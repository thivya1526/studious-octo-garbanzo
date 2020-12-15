Login.aspx
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.UI;
using System.Web.UI.WebControls;
using System.Data.SqlClient;
using System.Data;

namespace odts
{
    public partial class login : System.Web.UI.Page
    {
        SqlConnection con = new SqlConnection("Data Source=DESKTOP-NAJ8HHC;Initial Catalog=odts;Integrated Security=True");
        protected void Page_Load(object sender, EventArgs e)
        {

        }

        protected void submit_Click(object sender, EventArgs e)
        {
            if (uname.Text == "")
            {
                Response.Write("<script>alert('Enter username')</script>");

               //("Enter username", "Warning");
                uname.Focus();
            }
            else if (pswd.Text == "")
            {
                Response.Write("<script>alert('Enter password')</script>");
                pswd.Focus();
            }
            else if(type.Text=="Admin")
            {
                con.Open();
               //SqlCommand com = new SqlCommand("select * from admin_log where name='" 	+ uname.Text + "'and password='" + pswd.Text + "'", con);
                SqlCommand com = new SqlCommand("select * from admin_log where name='" + 	uname.Text + "'and password='" + pswd.Text + "'", con);
                SqlDataAdapter ad = new SqlDataAdapter(com);
                DataTable dt = new DataTable();
                ad.Fill(dt);
                if(dt.Rows.Count>0)
                {
                    Response.Write("<script>alert('Login Successfully')</script>");
                    Response.Redirect("WebForm1.aspx");
                }
                 
                else
                {
                    Response.Write("<script>alert('Login failed')</script>");
                }
                uname.Text = "";
                pswd.Text = "";
                
                con.Close();
            }
            else if(type.Text=="Operators")
            {
                con.Open();
                 SqlCommand cmd1 = new SqlCommand("select name, password,category from register where name='" + uname.Text +"' and password='"+pswd.Text+ "' and category = 'Operators' and status='Approve'", con);
                 SqlDataAdapter ad = new SqlDataAdapter(cmd1);
                // SqlDataReader dr = cmd1.ExecuteReader();
                 DataTable dt = new DataTable();
                 ad.Fill(dt);
     
                   //  while (dr.Read())
                   //  {
                          if (dt.Rows.Count > 0)
                         {
                             Session["id"] = uname.Text;
                           //Session["id"] = dt.GetValue(0).ToString();
                           Response.Write("<script>alert('WELCOME')</script>");
                           Response.Redirect("viewoperator.aspx");
                          }
                    // }
                    // dr.Close()

               else
                {
                    Response.Write("<script>alert('You Have No Permission to Access')</script>");
                }
                 uname.Text = "";
                 pswd.Text = "";

                 con.Close();
                
            }
            else if (type.Text == "Operational Admin")
            {
                con.Open();
                SqlCommand cmd2 = new SqlCommand("select name,password from register where name='" + uname.Text + "' and password='" + pswd.Text + "' and category = 'Operational Admin' and status='Approve'", con);
                SqlDataAdapter ad = new SqlDataAdapter(cmd2);
                DataTable dt = new DataTable();
                ad.Fill(dt);
                if (dt.Rows.Count > 0)
                {
                    Session["name"] = uname.Text;
                    Response.Write("<script>alert('WELCOME')</script>");
                    Response.Redirect("opadmin_view.aspx");
                }

                else
                {
                    Response.Write("<script>alert('You Have No Permission to Access')</script>");
                }
                uname.Text = "";
                pswd.Text = "";

                con.Close();
                
            }
            else
            {
                Response.Write("<script>alert('Please Select User Type!!')</script>");
 
            }
        }

        protected void LinkButton1_Click(object sender, EventArgs e)
        {
            Response.Redirect("register.aspx");
        }

        protected void cancel_Click(object sender, EventArgs e)
        {
            type.Text = "--Select Type--";
            uname.Text = "";
            pswd.Text = "";
        }

     
    }
}
Register.aspx
namespace odts
{
    public partial class register : System.Web.UI.Page
    {
        SqlConnection con = new SqlConnection(" Data Source=DESKTOP-NAJ8HHC;Initial Catalog=odts;Integrated Security=True");
        private string gender;

        protected void Page_Load(object sender, EventArgs e)
        {

            if (!IsPostBack)
            {
                Gender();
            }
        }

        private void Gender()
        {
            if (RadioButton1.Checked)
            {
                gender = "Male";
            }
            else if (RadioButton2.Checked)
            {
                gender = "Female";

            }
        }

        protected void Button1_Click(object sender, EventArgs e)

        {
            if (DropDownList1.Text == "Admin")
            {
                con.Open();
                ID = "pswd";
                
                //SqlCommand cmd = new SqlCommand("insert into admin_log (uname,category,gender,qual,desig,emailid,address,mblenum,password) values('" + uname.Text + "','" + DropDownList1.Text + "','" + gender + "','" + qual.Text + "','" + desig.Text + "','" + mailid.Text + "','" + add.Text + "','" + mble.Text + "','" + pswd.Text + "','Request')", con);
                SqlCommand cmd = new SqlCommand("insert into admin_log values('" + uname.Text + "','" + DropDownList1.Text + "','" + gender + "','" + qual.Text + "','" + desig.Text + "','" + mailid.Text + "','" + add.Text + "','" + mble.Text + "','" + pswd.Text + "','Request')", con);
                cmd.ExecuteNonQuery();
                cmd.Dispose();
                con.Close();
                Gender();
                Response.Redirect("login.aspx");
                //or
                Server.Transfer("login.aspx");
            }

            else if (DropDownList1.Text == "Operators")
            {

                con.Open();
                ID = "pswd";
               
                //SqlCommand cmd1 = new SqlCommand("insert into register (name,category,gender,qual,desig,emailid,address,mblenum,password) values('" + uname.Text + "','" + DropDownList1.Text + "','" + gender + "','" + qual.Text + "','" + desig.Text + "','" + mailid.Text + "','" + add.Text + "','" + mble.Text + "','" + pswd.Text + "','Request')", con);
                SqlCommand cmd1 = new SqlCommand("insert into register values('" + uname.Text + "','" + DropDownList1.Text + "','" + gender + "','" + qual.Text + "','" + desig.Text + "','" + mailid.Text + "','" + add.Text + "','" + mble.Text + "','" + pswd.Text + "','Request')", con);
                cmd1.ExecuteNonQuery();
                cmd1.Dispose();
                con.Close();
                Gender();
                Response.Redirect("login.aspx");
                //or
                Server.Transfer("login.aspx");
            }

            else if (DropDownList1.Text == "Operational Admin")

             {

                con.Open();
                ID = "pswd";

                //SqlCommand cmd2 = new SqlCommand("insert into register(name,category,gender,qual,desig,emailid,address,mblenum,password) values('" + uname.Text + "','" + DropDownList1.Text + "','" + gender + "','" + qual.Text + "','" + desig.Text + "','" + mailid.Text + "','" + add.Text + "','" + mble.Text + "','" + pswd.Text + "','Request')", con);
                SqlCommand cmd2 = new SqlCommand("insert into register values('" + uname.Text + "','" + DropDownList1.Text + "','" + gender + "','" + qual.Text + "','" + desig.Text + "','" + mailid.Text + "','" + add.Text + "','" + mble.Text + "','" + pswd.Text + "','Request')", con);
                cmd2.ExecuteNonQuery();
                cmd2.Dispose();
                con.Close();
                Gender();
                Response.Redirect("login.aspx");
                //or
                Server.Transfer("login.aspx");

            }



        }

    }       
}



Solve Query
namespace odts
{
    public partial class solve_query : System.Web.UI.Page
    {
        SqlConnection con = new SqlConnection(" Data Source=DESKTOP-NAJ8HHC;Initial Catalog=odts;Integrated Security=True");
        protected void Page_Load(object sender, EventArgs e)
        {
            con.Open();
           // SqlCommand cmd=new SqlCommand ("select defectid,language,defect,date,descri,solution from defect",con );
            SqlCommand cmd = new SqlCommand("select * from defect where solution!='Null'", con);
            cmd.ExecuteNonQuery();
            SqlDataAdapter da = new SqlDataAdapter(cmd);
            DataSet ds = new DataSet();
            da.Fill(ds, "defect");
            GridView1.DataSource = ds.Tables[0];
            GridView1.DataBind();
        }

        protected void GridView1_SelectedIndexChanged(object sender, EventArgs e)
        {

        }
    }
}
Track defect
namespace odts
{
    public partial class op_track : System.Web.UI.Page
    {
        SqlConnection con = new SqlConnection("Data Source=DESKTOP-NAJ8HHC;Initial Catalog=odts;Integrated Security=True");
        protected void Page_Load(object sender, EventArgs e)

        {
         
            
            con.Open();
            // SqlCommand cmd=new SqlCommand ("select defectid,language,defect,date,descri,solution from defect",con );
            SqlCommand cmd = new SqlCommand("select * from defect where solution='Null'", con);
            cmd.ExecuteNonQuery();
            SqlDataAdapter da = new SqlDataAdapter(cmd);
            DataSet ds = new DataSet();
            da.Fill(ds, "defect");
            GridView1.DataSource = ds.Tables[0];
            GridView1.DataBind();
            GridView1.Visible = true;
            cmd.Dispose();
            con.Close();
        }

      
        protected void Button1_Click(object sender, EventArgs e)
        {
            con.Open();
            SqlCommand cmdd = new SqlCommand("update defect set solution='"+TextBox3 .Text + "' where defectid='" + TextBox1 .Text +"'",con );
            cmdd.ExecuteNonQuery();
            cmdd.Dispose();
            Response.Redirect("op_view.aspx");
            //or
            Server.Transfer("op_view.aspx");

            clea();

            SqlCommand cmd = new SqlCommand("select * from defect where solution='Null'", con);
            cmd.ExecuteNonQuery();
            SqlDataAdapter da = new SqlDataAdapter(cmd);
            DataSet ds = new DataSet();
            da.Fill(ds, "defect");
            GridView1.DataSource = ds.Tables[0];
            GridView1.DataBind();
            GridView1.Visible = true;
            cmd.Dispose();
            con.Close();
        }

        private void clea()
        {
            TextBox1.Text = "";
            TextBox2.Text = "";
            TextBox3.Text = "";
        }

        protected void GridView1_SelectedIndexChanged1(object sender, EventArgs e)
        {
            TextBox1.Text = GridView1.SelectedRow.Cells[2].Text;
            TextBox2.Text = GridView1.SelectedRow.Cells[6].Text;
        }

      

        protected void cancel_Click1(object sender, EventArgs e)
        {
            clea();
        }

     
    }
}
Post Defect
namespace odts
{
    public partial class post_query : System.Web.UI.Page
    {
       
        SqlConnection con = new SqlConnection(" Data Source=DESKTOP-NAJ8HHC;Initial Catalog=odts;Integrated Security=True");
        
        protected void Page_Load(object sender, EventArgs e)
        {
            String name = (string)(Session["id"]);
             if (!IsPostBack)
              {
                GenerateAutoID();
                }
             name0.Text = name;

             TextBox4.Text = DateTime.Now.ToString("dd/MM/yyyy hh:mm tt");
        }


    private void GenerateAutoID()
        {
             con.Open();
             SqlCommand cmd = new SqlCommand("Select Count(defectid) from defect", con);
             int i = Convert.ToInt32(cmd.ExecuteScalar());
              con.Close();
             //i++;
            TextBox1.Text = i.ToString();
        }


    protected void Submit_Click(object sender, EventArgs e)
        {


            con.Open();
            //SqlCommand cmd = new SqlCommand("insert into defect (name,defectid,language,defect,date,descri) values('" + name0.Text + "','" + TextBox1.Text + "','" + DropDownList2.Text + "','" + DropDownList3.Text + "','" + TextBox4.Text + "','"+ TextBox2.Text + "')", con);
            SqlCommand cmd = new SqlCommand("insert into defect values('" + name0.Text + "','" + TextBox1.Text + "','" + DropDownList2.Text + "','" + DropDownList3.Text + "','" + TextBox4.Text + "','" + TextBox2.Text + "','Null')", con);

            cmd.ExecuteNonQuery();
            cmd.Dispose();
            con.Close();
            GenerateAutoID();

            Response.Redirect("viewoperator.aspx");
            //or
            Server.Transfer("viewoperator.aspx");
            Clea();
        }

        private void Clea()
        {
            TextBox1.Text = "";
            DropDownList2.Text = "";
            DropDownList3.Text = "";
            TextBox4.Text = "";
            TextBox2.Text = "";
        }

        

        protected void Cancel_Click1(object sender, EventArgs e)
        {
            Clea();
        }

        
    }
}
