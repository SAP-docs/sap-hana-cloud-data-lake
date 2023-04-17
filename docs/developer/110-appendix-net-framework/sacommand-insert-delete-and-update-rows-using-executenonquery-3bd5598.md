<!-- loio3bd5598e6c5f101487c0bb0d3e2e4077 -->

# SACommand: Insert, Delete, and Update Rows Using ExecuteNonQuery

To perform an insert, update, or delete with an SACommand object, use the ExecuteNonQuery method. The ExecuteNonQuery method issues a query \(SQL statement or stored procedure\) that does not return a result set.



You can only make changes \(inserts, updates, or deletes\) to data that is from a single table. You cannot update result sets that are based on joins. You must be connected to a database to use the SACommand object.

For information about obtaining primary key values for AUTOINCREMENT primary keys, see the documentation on retrieving primary key values for newly inserted rows.

To set the isolation level for a SQL statement, you must use the SACommand object as part of an SATransaction object. When you modify data without an SATransaction object, the provider operates in autocommit mode and any changes that you make are applied immediately.



## C\# ExecuteNonQuery DELETE and INSERT Example

The following example opens a connection to the sample database and uses the ExecuteNonQuery method to remove all departments whose ID is greater than or equal to 600 and then add two new rows to the Departments table. It displays the updated table in a datagrid.

```
SAConnection conn = new SAConnection(
    "Data Source=SAP IQ 17 Demo;Password="+pwd);
conn.Open();

SACommand deleteCmd = new SACommand(
    "DELETE FROM Departments WHERE DepartmentID >= 600",
    conn);
deleteCmd.ExecuteNonQuery();

SACommand insertCmd = new SACommand(
    "INSERT INTO Departments(DepartmentID, DepartmentName) VALUES( ?, ? )",
    conn );
SAParameter parm = new SAParameter();
parm.SADbType = SADbType.Integer;
insertCmd.Parameters.Add( parm );
parm = new SAParameter();
parm.SADbType = SADbType.Char;
insertCmd.Parameters.Add( parm );

insertCmd.Parameters[0].Value = 600;
insertCmd.Parameters[1].Value = "Eastern Sales";
int recordsAffected = insertCmd.ExecuteNonQuery();

insertCmd.Parameters[0].Value = 700;
insertCmd.Parameters[1].Value = "Western Sales";
recordsAffected = insertCmd.ExecuteNonQuery();

SACommand selectCmd = new SACommand(
    "SELECT * FROM Departments", conn );
SADataReader dr = selectCmd.ExecuteReader();

System.Windows.Forms.DataGrid dataGrid;
dataGrid = new System.Windows.Forms.DataGrid();
dataGrid.Location = new Point(15, 50);
dataGrid.Size = new Size(275, 200);
dataGrid.CaptionText = "SACommand Example";
this.Controls.Add(dataGrid);

dataGrid.DataSource = dr;
dr.Close();
conn.Close();
```



## C\# ExecuteNonQuery UPDATE Example

The following example opens a connection to the sample database and uses the ExecuteNonQuery method to update the DepartmentName column to "Engineering" in all rows of the Departments table where the DepartmentID is 100. It displays the updated table in a datagrid.

```
SAConnection conn = new SAConnection(
    "Data Source=SAP IQ 17 Demo;Password="+pwd);
conn.Open();

SACommand updateCmd = new SACommand(
    "UPDATE Departments SET DepartmentName = 'Engineering' " +
    "WHERE DepartmentID = 100", conn );
int recordsAffected = updateCmd.ExecuteNonQuery();

SACommand selectCmd = new SACommand(
    "SELECT * FROM Departments", conn );
SADataReader dr = selectCmd.ExecuteReader();

System.Windows.Forms.DataGrid dataGrid;
dataGrid = new System.Windows.Forms.DataGrid();
dataGrid.Location = new Point(15, 50);
dataGrid.Size = new Size(275, 200);
dataGrid.CaptionText = "SACommand Example";
this.Controls.Add(dataGrid);

dataGrid.DataSource = dr;
dr.Close();
conn.Close();
```

