<!-- loio3bd0cbfc6c5f1014a4288ffa24aeedc7 -->

# SADataAdapter: Format a DataTable Using FillSchema

The SADataAdapter allows you to configure the schema of a DataTable to match that of a specific query using the FillSchema method. The attributes of the columns in the DataTable will match those of the SelectCommand of the SADataAdapter object.



Unlike the Fill method, no rows are stored in the DataTable.



## C\# SADataAdapter FillSchema Example Using a DataTable

The following example shows how to use the FillSchema method to set up a new DataTable object with the same schema as a result set. The Additions DataTable is then bound to the grid on the screen.

```
SAConnection conn = new SAConnection( "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
SADataAdapter da = new SADataAdapter("SELECT * FROM Employees", conn);
DataTable dt = new DataTable("Additions");
da.FillSchema(dt, SchemaType.Source);
conn.Close();
dataGridView1.DataSource = dt;
```



## C\# SADataAdapter FillSchema Example Using a DataSet

The following example shows how to use the FillSchema method to set up a new DataTable object with the same schema as a result set. The DataTable is added to the DataSet using the Merge method. The Additions DataTable is then bound to the grid on the screen.

```
SAConnection conn = new SAConnection( "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
SADataAdapter da = new SADataAdapter("SELECT * FROM Employees", conn);
DataTable dt = new DataTable("Additions");
da.FillSchema(dt, SchemaType.Source);
DataSet ds = new DataSet();
ds.Merge(dt);
conn.Close();
dataGridView1.DataSource = ds.Tables["Additions"];
```

