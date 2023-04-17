<!-- loio3c0f3f9b6c5f101484ee98bc87173251 -->

# EndExecuteNonQuery\(IAsyncResult\) Method

Finishes asynchronous execution of a SQL statement or stored procedure.



Visual Basic
:   ```
Public Function EndExecuteNonQuery (ByVal asyncResult As IAsyncResult) As Integer
```

C\#
:   ```
public unsafe int EndExecuteNonQuery (IAsyncResult asyncResult)
```



## Parameters

asyncResult
:   The IAsyncResult returned by the call to SACommand.BeginExecuteNonQuery.



## Returns

The number of rows affected \(the same behavior as SACommand.ExecuteNonQuery\).



## Exceptions

ArgumentException
:   The asyncResult parameter is null \(Nothing in Microsoft Visual Basic\).

InvalidOperationException
:   The SACommand.EndExecuteNonQuery\(IAsyncResult\) was called more than once for a single command execution, or the method was mismatched against its execution method.



## Remarks

Call EndExecuteNonQuery once for every call to BeginExecuteNonQuery. The call must be after BeginExecuteNonQuery has returned. ADO.NET is not thread safe; it is your responsibility to ensure that BeginExecuteNonQuery has returned. The IAsyncResult passed to EndExecuteNonQuery must be the same as the one returned from the BeginExecuteNonQuery call that is being completed. It is an error to call EndExecuteNonQuery to end a call to BeginExecuteReader, and vice versa.

If an error occurs while executing the command, then the exception is thrown when EndExecuteNonQuery is called.

There are four ways to wait for execution to complete:

\(1\) Call EndExecuteNonQuery.

Calling EndExecuteNonQuery blocks until the command completes. For example:

```
SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
conn.Open();
SACommand cmd = new SACommand( 
   "UPDATE Departments"
	+ " SET DepartmentName = 'Engineering'"
	+ " WHERE DepartmentID=100",
   conn );
IAsyncResult res = cmd.BeginExecuteNonQuery();
// perform other work
// this will block until the command completes
int rowCount = cmd.EndExecuteNonQuery( res );
```

\(2\) Poll the IsCompleted property of the IAsyncResult.

For example:

```
SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
conn.Open();
SACommand cmd = new SACommand( 
   "UPDATE Departments"
	+ " SET DepartmentName = 'Engineering'"
	+ " WHERE DepartmentID=100",
   conn );
IAsyncResult res = cmd.BeginExecuteNonQuery();
while( !res.IsCompleted ) {
   // do other work
}
// this will not block because the command is finished
int rowCount = cmd.EndExecuteNonQuery( res );
```

\(3\) Use the IAsyncResult.AsyncWaitHandle property to get a synchronization object, and wait on that.

For example:

```
SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
conn.Open();
SACommand cmd = new SACommand( 
   "UPDATE Departments"
	+ " SET DepartmentName = 'Engineering'"
	+ " WHERE DepartmentID=100",
   conn );
IAsyncResult res = cmd.BeginExecuteNonQuery();
// perform other work
WaitHandle wh = res.AsyncWaitHandle;
wh.WaitOne();
// this will not block because the command is finished
int rowCount = cmd.EndExecuteNonQuery( res );
```

\(4\) Specify a callback function when calling BeginExecuteNonQuery.

For example:

```
private void callbackFunction( IAsyncResult ar ) {
   SACommand cmd = (SACommand) ar.AsyncState;
   // this won't block since the command has completed
   int rowCount = cmd.EndExecuteNonQuery( ar );
}

// elsewhere in the code
private void DoStuff() {
   SAConnection conn = new SAConnection("DSN=SQL Anywhere 17 Demo");
   conn.Open();
   SACommand cmd = new SACommand(
	"UPDATE Departments"
	    + " SET DepartmentName = 'Engineering'"
	    + " WHERE DepartmentID=100",
	conn );
   IAsyncResult res = cmd.BeginExecuteNonQuery( callbackFunction, cmd );
   // perform other work.  The callback function is 
   // called when the command completes
}
```

The callback function executes in a separate thread, so the usual caveats related to updating the user interface in a threaded program apply.

**Related Information**  


[BeginExecuteNonQuery\(\) Method](beginexecutenonquery-method-3c0e94a.md "Initiates the asynchronous execution of a SQL statement or stored procedure that is described by this SACommand.")

