<!-- loio3bd64ea76c5f1014a91892a52cd0f9d9 -->

# SACommand: Fetch Result Set Schema Using GetSchemaTable

You can obtain schema information about columns in a result set using the GetSchemaTable method.



The GetSchemaTable method of the SADataReader class obtains information about the current result set. The GetSchemaTable method returns the standard .NET DataTable object, which provides information about all the columns in the result set, including column properties.



## C\# Schema Information Example

The following example obtains information about a result set using the GetSchemaTable method and binds the DataTable object to the datagrid on the screen.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
SACommand cmd = new SACommand("SELECT * FROM Employees", conn);
SADataReader reader = cmd.ExecuteReader();
DataTable schema = reader.GetSchemaTable();
reader.Close();
conn.Close();
dataGridView1.DataSource = schema;
```

