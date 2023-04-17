<!-- loio3bd0c3df6c5f1014a41588abad614fa0 -->

# SADataAdapter: Fetch Data into a DataTable Using Fill

The SADataAdapter allows you to view a result set by using the Fill method to fill a DataTable with the results from a query and then binding the DataTable to a display grid.



When setting up an SADataAdapter, you can specify a SQL statement that returns a result set. When Fill is called to populate a DataTable, all the rows are fetched in one operation using a forward-only, read-only cursor. Once all the rows in the result set have been read, the cursor is closed. Changes made to the rows in a DataTable can be reflected to the database using the Update method.

You can use the SADataAdapter object to retrieve a result set that is based on a join. However, you can only make changes \(inserts, updates, or deletes\) to data that is from a single table. You cannot update result sets that are based on joins.

> ### Caution:  
> Any changes you make to a DataTable are made independently of the original database table. Your application does not have locks on these rows in the database. Your application must be designed to resolve any conflicts that may occur when changes from the DataTable are applied to the database if another user changes the data you are modifying before your changes are applied to the database.



## C\# SADataAdapter Fill Example Using a DataTable

The following example shows how to fill a DataTable using the SADataAdapter. It creates a new DataTable object named Results and a new SADataAdapter object. The SADataAdapter Fill method is used to fill the DataTable with the results of the query. The DataTable is then bound to the grid on the screen.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
DataTable dt = new DataTable("Results");
SADataAdapter da = new SADataAdapter("SELECT * FROM Employees", conn);
da.Fill(dt);
conn.Close();
dataGridView1.DataSource = dt;
```



## C\# SADataAdapter Fill Example Using a DataSet

The following example shows how to fill a DataTable using the SADataAdapter. It creates a new DataSet object and a new SADataAdapter object. The SADataAdapter Fill method is used to create a DataTable table named Results in the DataSet and then fill it with the results of the query. The Results DataTable is then bound to the grid on the screen.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
DataSet ds = new DataSet();
SADataAdapter da = new SADataAdapter("SELECT * FROM Employees", conn);
da.Fill(ds, "Results");
conn.Close();
dataGridView1.DataSource = ds.Tables["Results"];
```

