<!-- loio3c1e473f6c5f1014b42cf3dc386447d9 -->

# Connection Property

Provides the SAConnection object required to execute SQL on the database server.



Visual Basic
:   ```
Public Shared ReadOnly Property Connection As SAConnection
```

C\#
:   ```
public SAConnection Connection {get;}
```



## Remarks

The connection is already established to the database server. It is not necessary to use SAConnection to establish a connection. Obtain the connection object using a statement similar to the following:

SAConnection \_conn = SAServerSideConnection.Connection;



The following example obtains the SAConnection object and then executes a SQL statement to create a table.

```
using Sap.Data.SQLAnywhere;
using Sap.SQLAnywhere.Server;

SAConnection _conn = SAServerSideConnection.Connection;
SACommand cmd = _conn.CreateCommand();
cmd.CommandText = "CREATE TABLE Tab( c1 int, c2 char(128), c3 smallint, c4 double, c5 numeric(30,6) )";
cmd.ExecuteNonQuery();
cmd.Dispose();
```

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

