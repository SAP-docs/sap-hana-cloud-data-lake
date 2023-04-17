<!-- loio3bd3ce566c5f101489ad95a573c20a0f -->

# SACommand: Fetch Data Using ExecuteReader and ExecuteScalar

The SACommand object allows you to execute a SQL statement or call a stored procedure against a database. You can use the ExecuteReader or ExecuteScalar methods to retrieve data from the database.



 ExecuteReader
 :   Issues a SQL query that returns a result set. This method uses a forward-only, read-only cursor. You can loop quickly through the rows of the result set in one direction.

  ExecuteScalar
 :   Issues a SQL query that returns a single value. This can be the first column in the first row of the result set, or a SQL statement that returns an aggregate value such as COUNT or AVG. This method uses a forward-only, read-only cursor.

 When using the SACommand object, you can use the SADataReader to retrieve a result set that is based on a join. However, you can only make changes \(inserts, updates, or deletes\) to data that is from a single table. You cannot update result sets that are based on joins.

When using the SADataReader, there are several Get methods available that you can use to return the results in the specified data type.



## Microsoft C\# ExecuteReader Example

The following Microsoft C\# code opens a connection to the sample database and uses the ExecuteReader method to create a result set containing the last names of employees in the Employees table:

```
SAConnection conn = new SAConnection(
    "Data Source=SAP IQ 17 Demo;Password="+pwd);
conn.Open();
SACommand cmd = new SACommand("SELECT Surname FROM Employees", conn);
SADataReader reader = cmd.ExecuteReader();
listEmployees.BeginUpdate();
while (reader.Read())
{
    listEmployees.Items.Add(reader.GetString(0));
}
listEmployees.EndUpdate();
reader.Close();
conn.Close();
```



## Microsoft Visual Basic ExecuteReader Example

The following Microsoft Visual Basic code opens a connection to the sample database and uses the ExecuteReader method to create a result set containing the last names of employees in the Employees table:

```
Dim conn As New SAConnection("Data Source=SAP IQ 17 Demo;Password="+pwd)
conn.Open()
Dim cmd As New SACommand("SELECT Surname FROM Employees", conn)
Dim reader As SADataReader = cmd.ExecuteReader()
ListEmployees.BeginUpdate()
Do While (reader.Read())
    ListEmployees.Items.Add(reader.GetString(0))
Loop
ListEmployees.EndUpdate()
reader.Close()
conn.Close()
```



## Microsoft C\# ExecuteScalar Example

The following Microsoft C\# code opens a connection to the sample database and uses the ExecuteScalar method to obtain a count of the number of male employees in the Employees table:

```
SAConnection conn = new SAConnection(
    "Data Source=SAP IQ 17 Demo;Password="+pwd);
conn.Open();
SACommand cmd = new SACommand(
    "SELECT COUNT(*) FROM Employees WHERE Sex = 'M'", conn );
int count = (int) cmd.ExecuteScalar();
textBox1.Text = count.ToString();
conn.Close();
```

