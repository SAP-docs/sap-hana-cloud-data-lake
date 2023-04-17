<!-- loio3c1e4f676c5f101485a6db1d052fa946 -->

# SAServerSideConnection Class

Represents a server-side connection to a database.



Visual Basic
:   ```
Public NotInheritable Class SAServerSideConnection
```

C\#
:   ```
public sealed class SAServerSideConnection
```



## Members

All members of SAServerSideConnection, including inherited members.

 **Properties** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Property



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public SAConnection



</td>
<td valign="top">

 [Connection](connection-property-3c1e473.md) 



</td>
<td valign="top">

Provides the SAConnection object required to execute SQL on the database server.



</td>
</tr>
</table>



## Remarks

This class supports the execution of server-side SQL from the CLR external environment. A CLR function or method called from the database server can call back into the database server. A connection is already established to the database server. It is not necessary to use SAConnection to establish a connection.

