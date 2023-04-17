<!-- loio3bd312756c5f1014a2a4d4baffb0d68b -->

# Microsoft .NET Error Handling

Your application should be designed to handle any errors that occur. An SAException object is created when an exception is thrown. Information about the exception is stored in the SAException object.



The data lake Relational Engine .NET Data Provider creates an SAException object and throws an exception whenever errors occur during execution. Each SAException object consists of a list of SAError objects, and these error objects include the error message and code.

Errors are different from conflicts. Conflicts arise when changes are applied to the database. Your application should include a process to compute correct values or to log conflicts when they arise.



## Microsoft C\# Error Handling Example

The following Microsoft C\# code creates a button click handler that opens a connection to the sample database. If the connection cannot be made, the exception handler displays one or more messages.

```
private void button1_Click(object sender, EventArgs e)
{
    SAConnection conn = new SAConnection(
        "Data Source=SAP IQ 17 Demo;Password="+pwd);
    try
    {
        conn.Open();
    }
    catch (SAException ex)
    {
        for (int i = 0; i < ex.Errors.Count; i++)
        {
            MessageBox.Show(ex.Errors[i].Source + " : " +
             ex.Errors[i].Message + " (" +
             ex.Errors[i].NativeError.ToString() + ")",
             "Failed to connect");
        }
    }
    catch (Exception ex)
    {
        MessageBox.Show(ex.Message, "Failed to connect");
    }
}
```



## Microsoft Visual Basic Error Handling Example

The following Microsoft Visual Basic code creates a button click handler that opens a connection to the sample database. If the connection cannot be made, then the exception handler displays one or more messages.

```
Private Sub Button1_Click(ByVal sender As System.Object, _
     ByVal e As System.EventArgs) Handles Button1.Click
    Dim conn As New SAConnection("Data Source=SAP IQ 17 Demo;Password="+pwd)
    Try
        conn.Open()
    Catch ex As SAException
        For i = 0 To ex.Errors.Count - 1
            MessageBox.Show(ex.Errors(i).Source & " : " & _
              ex.Errors(i).Message & " (" & _
              ex.Errors(i).NativeError.ToString() & ")", _
              "Failed to connect")
        Next i
    Catch ex as Exception
        MessageBox.Show(ex.Message, "Failed to connect")
    End Try
End Sub
```

