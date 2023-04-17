<!-- loio3be15fc06c5f1014ab73baea7947987d -->

# Stored Procedures

You can use SQL stored procedures with the SQL Anywhere .NET Data Provider.



The ExecuteReader method is used to call stored procedures that return result sets, while the ExecuteNonQuery method is used to call stored procedures that do not return any result sets. The ExecuteScalar method is used to call stored procedures that return only a single value.

You can use SAParameter objects to pass parameters to a stored procedure.



## C\# Stored Procedure Call with Parameters Example

The following example shows two ways to call a stored procedure and pass it a parameter. The example uses an SADataReader to fetch the result set returned by the stored procedure.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
bool method1 = true;

SACommand cmd = new SACommand("", conn);
if (method1)
{
    cmd.CommandText = "ShowProductInfo";
    cmd.CommandType = CommandType.StoredProcedure;
}
else
{
    cmd.CommandText = "call ShowProductInfo(?)";
    cmd.CommandType = CommandType.Text;
}

SAParameter param = cmd.CreateParameter();
param.SADbType = SADbType.Integer;
param.Direction = ParameterDirection.Input;
param.Value = 301;
cmd.Parameters.Add(param);

SADataReader reader = cmd.ExecuteReader();
reader.Read();
int ID = reader.GetInt32(0);
string name = reader.GetString(1);
string description = reader.GetString(2);
decimal price = reader.GetDecimal(6);
reader.Close();

listBox1.BeginUpdate();
listBox1.Items.Add("Name=" + name +
    " Description=" + description + " Price=" + price);
listBox1.EndUpdate();

conn.Close();
```

