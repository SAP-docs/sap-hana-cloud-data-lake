<!-- loio3bd046166c5f10148206f610273b726c -->

# Microsoft .NET Database Connections

To connect to a database, an SAConnection object must be created. The connection string can be specified when creating the object or it can be established later by setting the ConnectionString property.



A well-designed application should handle any errors that occur when attempting to connect to a database.

A connection to the database is created when the connection is opened and released when the connection is closed.



## Microsoft C\# SAConnection Example

The following Microsoft C\# code creates a button click handler that opens a connection to the sample database and then closes it. An exception handler is included.

```
private void button1_Click(object sender, EventArgs e)
{
    SAConnection conn = new SAConnection("Data Source=SAP IQ 17 Demo;Password="+pwd);
    try
    {
        conn.Open();

        conn.Close();
    }
    catch (SAException ex)
    {
        MessageBox.Show(ex.Errors[0].Source + " : " +
             ex.Errors[0].Message + " (" +
             ex.Errors[0].NativeError.ToString() + ")",
             "Failed to connect");
    }
    catch (Exception ex)
    {
        MessageBox.Show(ex.Message, "Failed to connect");
    }
}
```



## Microsoft Visual Basic SAConnection Example

The following Microsoft Visual Basic code creates a button click handler that opens a connection to the sample database and then closes it. An exception handler is included.

```
Private Sub Button1_Click(ByVal sender As System.Object, _
     ByVal e As System.EventArgs) Handles Button1.Click
    Dim conn As New SAConnection("Data Source=SAP IQ 17 Demo;Password="+pwd)
    Try
        conn.Open()

        conn.Close()
    Catch ex As SAException
        MessageBox.Show(ex.Errors(0).Source & " : " & _
                 ex.Errors(0).Message & " (" & _
                 ex.Errors(0).NativeError.ToString() & ")", _
                 "Failed to connect")
    Catch ex as Exception
        MessageBox.Show(ex.Message, "Failed to connect")
    End Try
End Sub
```

