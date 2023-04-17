<!-- loio3be3a1e76c5f1014bf68bf7419f899c2 -->

# The Table Viewer Sample Project Explained

By examining the code from the Table Viewer project, some key features of the SQL Anywhere .NET Data Provider are illustrated.

The Table Viewer project uses the sample database, <code><i>iqdemo.db</i></code>, which is located in the samples directory.

The Table Viewer project is described a few lines at a time. Not all code from the sample is included here. To see all the code, open the project file <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ADO.NET\TableViewer\TableViewer.sln</code>.



## Declaring Controls

The following code declares a couple of Labels named label1 and label2, a TextBox named txtConnectString, a button named btnConnect, a TextBox named txtSQLStatement, a button named btnExecute, and a DataGrid named dgResults.

```
private System.Windows.Forms.Label label1;
private System.Windows.Forms.TextBox txtConnectString;
private System.Windows.Forms.Label label2;
private System.Windows.Forms.Button btnConnect;
private System.Windows.Forms.TextBox txtSQLStatement;
private System.Windows.Forms.Button btnExecute;
private System.Windows.Forms.DataGrid dgResults;
```



## Declaring a Connection Object

The SAConnection type is used to declare an uninitialized connection object. The SAConnection object is used to represent a unique connection to a data source.

```
private SAConnection _conn;
```



## Connecting to the Database

The Text property of the txtConnectString object has a default value of "Data Source=SAP IQ 17 Demo;Password=sql". This value can be overridden by the application user by typing a new value into the txtConnectString text box. You can see how this default value is set by opening up the region in `TableViewer.cs` labeled Windows Form Designer Generated Code. In this region, you find the following line of code.

```
this.txtConnectString.Text = "Data Source=SAP IQ 17 Demo;Password=passwd";
```

Later, the SAConnection object uses the connection string to connect to a database. The following code creates a new connection object with the connection string using the SAConnection constructor. It then establishes the connection by using the Open method.

```
_conn = new SAConnection( txtConnectString.Text );
_conn.Open();
```



## Defining a Query

The Text property of the txtSQLStatement object has a default value of "SELECT \* FROM Employees". This value can be overridden by the application user by typing a new value into the txtSQLStatement text box.

The SQL statement is executed using an SACommand object. The following code declares and creates a command object using the SACommand constructor. This constructor accepts a string representing the query to be executed, along with the SAConnection object that represents the connection that the query is executed on.

```
SACommand cmd = new SACommand( txtSQLStatement.Text.Trim(), _conn );
```



## Displaying the Results

The results of the query are obtained using an SADataReader object. The following code declares and creates an SADataReader object using the ExecuteReader constructor. This constructor is a member of the SACommand object, cmd, that was declared previously. ExecuteReader sends the command text to the connection for execution and builds an SADataReader.

```
SADataReader dr = cmd.ExecuteReader();
```

The following code connects the SADataReader object to the DataGrid object, which causes the result columns to appear on the screen. The SADataReader object is then closed.

```
dgResults.DataSource = dr;
dr.Close();
```



## Error Handling

If there is an error when the application attempts to connect to the database or when it populates the tables combo box, the following code catches the error and displays its message:

```
try
{
  _conn = new SAConnection( txtConnectString.Text );
  _conn.Open();

  SACommand cmd = new SACommand( "SELECT table_name FROM sys.systable " +
      "WHERE creator = 101 AND table_type != 'TEXT'", _conn );
  SADataReader   dr = cmd.ExecuteReader();

  comboBoxTables.Items.Clear();
  while ( dr.Read() )
  {
    comboBoxTables.Items.Add( dr.GetString( 0 ) );
  }
  dr.Close();
} 
catch( SAException ex )
{
  MessageBox.Show( ex.Errors[0].Source + " : " + ex.Errors[0].Message + " (" +
                   ex.Errors[0].NativeError.ToString() + ")",
                   "Failed to connect" );
}
```

