<!-- loio3c0f47716c5f10149015e341e81bd149 -->

# EndExecuteReader\(IAsyncResult\) Method

Finishes asynchronous execution of a SQL statement or stored procedure, returning the requested SADataReader.



Visual Basic
:   ```
Public Function EndExecuteReader (ByVal asyncResult As IAsyncResult) As SADataReader
```

C\#
:   ```
public unsafe SADataReader EndExecuteReader (IAsyncResult asyncResult)
```



## Parameters

asyncResult
:   The IAsyncResult returned by the call to SACommand.BeginExecuteReader.



## Returns

An SADataReader object that can be used to retrieve the requested rows \(the same behavior as SACommand.ExecuteReader\).



## Exceptions

ArgumentException
:   The asyncResult parameter is null \(Nothing in Microsoft Visual Basic\)

InvalidOperationException
:   The SACommand.EndExecuteReader\(IAsyncResult\) was called more than once for a single command execution, or the method was mismatched against its execution method.



## Remarks

Call EndExecuteReader once for every call to BeginExecuteReader. The call must be after BeginExecuteReader has returned. ADO.NET is not thread safe; it is your responsibility to ensure that BeginExecuteReader has returned. The IAsyncResult passed to EndExecuteReader must be the same as the one returned from the BeginExecuteReader call that is being completed. It is an error to call EndExecuteReader to end a call to BeginExecuteNonQuery, and vice versa.

If an error occurs while executing the command, then the exception is thrown when EndExecuteReader is called.

There are four ways to wait for execution to complete:

\(1\) Call EndExecuteReader.

Calling EndExecuteReader blocks until the command completes. For example:

```
SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
conn.Open();
SACommand cmd = new SACommand( "SELECT * FROM Departments", conn );
IAsyncResult res = cmd.BeginExecuteReader();
// perform other work
// this blocks until the command completes
SADataReader reader = cmd.EndExecuteReader( res );
```

\(2\) Poll the IsCompleted property of the IAsyncResult.

For example:

```
SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
conn.Open();
SACommand cmd = new SACommand( "SELECT * FROM Departments", conn );
IAsyncResult res = cmd.BeginExecuteReader();
while( !res.IsCompleted ) {
   // do other work
}
// this does not block because the command is finished
SADataReader reader = cmd.EndExecuteReader( res );
```

\(3\) Use the IAsyncResult.AsyncWaitHandle property to get a synchronization object, and wait on that.

For example:

```
SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
conn.Open();
SACommand cmd = new SACommand( "SELECT * FROM Departments", conn );
IAsyncResult res = cmd.BeginExecuteReader();
// perform other work
WaitHandle wh = res.AsyncWaitHandle;
wh.WaitOne();
// this does not block because the command is finished
SADataReader reader = cmd.EndExecuteReader( res );
```

\(4\) Specify a callback function when calling BeginExecuteReader

For example:

```
private void callbackFunction( IAsyncResult ar ) {
   SACommand cmd = (SACommand) ar.AsyncState;
   // this does not block since the command has completed
   SADataReader reader = cmd.EndExecuteReader();
}

// elsewhere in the code
private void DoStuff() {
   SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
   conn.Open();
   SACommand cmd = new SACommand( "SELECT * FROM Departments", conn );
   IAsyncResult res = cmd.BeginExecuteReader( callbackFunction, cmd );
   // perform other work.  The callback function is 
   // called when the command completes
}
```

The callback function executes in a separate thread, so the usual caveats related to updating the user interface in a threaded program apply.

**Related Information**  


[BeginExecuteReader\(\) Method](beginexecutereader-method-3c0eab9.md "Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand, and retrieves one or more result sets from the database server.")

[SADataReader Class](sadatareader-class-3c181c1.md "A read-only, forward-only result set from a query or stored procedure.")

