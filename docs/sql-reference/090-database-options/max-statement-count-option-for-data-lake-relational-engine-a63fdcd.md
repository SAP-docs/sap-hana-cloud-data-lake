<!-- loioa63fdcdd84f21015a371fc8cb0f59098 -->

# MAX\_STATEMENT\_COUNT Option for Data Lake Relational Engine

Specifies a resource governor to limit the maximum number of prepared statements that a connection can use at once.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63fdcdd84f21015a371fc8cb0f59098__iq_refso_759"/>

## Default

100



<a name="loioa63fdcdd84f21015a371fc8cb0f59098__iq_refso_761"/>

## Remarks

This options limits the number of prepared statements per connection that a user can have. If an operation exceeds the limit for a connection, an error is generated indicating that the limit has been exceeded.

If a connection executes a stored procedure, the procedure is executed under the permissions of the procedure owner. However, the resources used by the procedure are assigned to the current connection.

