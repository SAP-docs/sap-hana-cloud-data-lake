<!-- loio9cf12cd0a7d31014ac09c92e186adb3b -->

# a\_sqlany\_callback\_type Enumeration

An enumeration of the callback types.



```
enum a_sqlany_callback_type
```



## Members


<table>
<tr>
<th valign="top">

Member name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

CALLBACK\_START



</td>
<td valign="top">

This function is called just before a database request is sent to the server.

CALLBACK\_START is used only on Windows operating systems.



</td>
</tr>
<tr>
<td valign="top">

CALLBACK\_WAIT



</td>
<td valign="top">

This function is called repeatedly by the interface library while the database server or client library is busy processing your database request.



</td>
</tr>
<tr>
<td valign="top">

CALLBACK\_FINISH



</td>
<td valign="top">

This function is called after the response to a database request has been received by the DBLIB interface DLL.

CALLBACK\_FINISH is used only on Windows operating systems.



</td>
</tr>
<tr>
<td valign="top">

CALLBACK\_MESSAGE



</td>
<td valign="top">

This function is called when messages are received from the server during the processing of a request.

Messages can be sent to the client application from the database server using the SQL MESSAGE statement. Messages can also be generated by long running database server statements.



</td>
</tr>
<tr>
<td valign="top">

CALLBACK\_CONN\_DROPPED



</td>
<td valign="top">

This function is called when the database server is about to drop a connection because of a liveness timeout, through a DROP CONNECTION statement, or because the database server is being shut down.

The connection name conn\_name is passed in to allow you to distinguish between connections. If the connection was not named, it has a value of NULL.



</td>
</tr>
<tr>
<td valign="top">

CALLBACK\_DEBUG\_MESSAGE



</td>
<td valign="top">

This function is called once for each debug message and is passed a null-terminated string containing the text of the debug message.

A debug message is a message that is logged to the LogFile file. In order for a debug message to be passed to this callback, the LogFile connection parameter must be used. The string normally has a newline character \(\) immediately before the terminating null character.



</td>
</tr>
<tr>
<td valign="top">

CALLBACK\_VALIDATE\_FILE\_TRANSFER



</td>
<td valign="top">

This function is called when a file transfer requires validation.

If the client data transfer is being requested during the execution of indirect statements such as from within a stored procedure, the client library will not allow a transfer unless the client application has registered a validation callback and the response from the callback indicates that the transfer may take place.



</td>
</tr>
</table>



## Remarks

The callback types correspond to the embedded SQL callback types.

**Related Information**  


[sqlany\_register\_callback\(a\_sqlany\_connection \*, a\_sqlany\_callback\_type, SQLANY\_CALLBACK\_PARM\) Method](sqlany-register-callback-a-sqlany-connection-a-sqlany-callback-type-sqlany-callback-pa-3bf6a9c.md "Register a callback routine.")
