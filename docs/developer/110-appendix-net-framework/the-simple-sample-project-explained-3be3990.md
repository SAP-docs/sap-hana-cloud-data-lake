<!-- loio3be399066c5f1014818ee828338e2588 -->

# The Simple Sample Project Explained

By examining the code from the Simple project, some key features of the SQL Anywhere .NET Data Provider are illustrated.

The Simple project uses the sample database, <code><i>iqdemo.db</i></code>, which is located in your samples directory.

The Simple project is described a few lines at a time. Not all code from the sample is included here. To see all the code, open the project file <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\ADO.NET\SimpleWin32\Simple.sln</code>.



## Declaring Controls

The following code declares a textbox named txtConnectString, a button named btnConnect, and a listbox named listEmployees.

```
private System.Windows.Forms.TextBox txtConnectString;
private System.Windows.Forms.Button btnConnect;
private System.Windows.Forms.ListBox listEmployees;
```



## Connecting to the Database

The btnConnect\_Click method declares and initializes an SAConnection connection object.

```
SAConnection conn = new SAConnection("Data Source=SAP IQ 17 Demo;"
    + txtConnectString.Text);
```

The SAConnection object uses the connection string to connect to the sample database when the Open method is called.

```
conn.Open();
```



## Defining a Query

A SQL statement is executed using an SACommand object. The following code declares and creates a command object using the SACommand constructor. This constructor accepts a string representing the query to be executed, along with the SAConnection object that represents the connection that the query is executed on.

```
SACommand cmd = new SACommand("SELECT Surname FROM Employees", conn);
```



## Displaying the Results

The results of the query are obtained using an SADataReader object. The following code declares and creates an SADataReader object using the ExecuteReader constructor. This constructor is a member of the SACommand object, cmd, that was declared previously. ExecuteReader sends the command text to the connection for execution and builds an SADataReader.

```
SADataReader reader = cmd.ExecuteReader();
```

The following code loops through the rows held in the SADataReader object and adds them to the listbox control. Each time the Read method is called, the data reader gets another row back from the result set. A new item is added to the listbox for each row that is read. The data reader uses the GetString method with an argument of 0 to get the first column from the result set row.

```
listEmployees.BeginUpdate();
while( reader.Read() )
{
    listEmployees.Items.Add(reader.GetString(0));
}
listEmployees.EndUpdate();
```



## Finishing Off

The following code at the end of the method closes the data reader and connection objects.

```
reader.Close();
conn.Close();
```



## Error Handling

Any errors that occur during execution and that originate with .NET Data Provider objects are handled by displaying them in a window. The following code catches the error and displays its message:

```
catch (SAException ex)
{
    MessageBox.Show(ex.Errors[0].Message);
}
```

