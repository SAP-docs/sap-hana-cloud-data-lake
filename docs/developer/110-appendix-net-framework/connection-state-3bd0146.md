<!-- loio3bd014696c5f10148733bb96ef656efe -->

# Connection State

Once your application has established a connection to the database, you can check the connection state to ensure that the connection is still open before communicating a request to the database server.

If a connection is closed, you can return an appropriate message to the user and/or attempt to reopen the connection.

The SAConnection class has a State property that can be used to check the state of the connection. Possible state values are ConnectionState.Open and ConnectionState.Closed.

The following code checks whether the SAConnection object has been initialized, and if it has, it checks that the connection is open. A message is returned to the user if the connection is not open.

```
if ( conn == null || conn.State != ConnectionState.Open ) 
{
    MessageBox.Show( "Connect to a database first", "Not connected" );
    return;
} 
```

