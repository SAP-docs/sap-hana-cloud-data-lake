<!-- loio3c0f66736c5f1014b53ea532765eff57 -->

# ExecuteReader\(CommandBehavior\) Method

Executes a SQL statement that returns a result set.



Visual Basic
:   ```
Public Shadows Function ExecuteReader (ByVal behavior As CommandBehavior) As SADataReader
```

C\#
:   ```
public new SADataReader ExecuteReader (CommandBehavior behavior)
```



## Parameters

behavior
:   One of CloseConnection, Default, KeyInfo, SchemaOnly, SequentialAccess, SingleResult, or SingleRow. For more information about this parameter, see the .NET Framework documentation for CommandBehavior Enumeration.



## Returns

The result set as an SADataReader object.



## Remarks

The statement is the current SACommand object, with CommandText and Parameters as needed. The SADataReader object is a read-only, forward-only result set. For modifiable result sets, use an SADataAdapter.

**Related Information**  


[ExecuteNonQuery\(\) Method](executenonquery-method-3c0f56f.md "Executes a statement that does not return a result set, such as an INSERT, UPDATE, DELETE, or data definition statement.")

[SADataReader Class](sadatareader-class-3c181c1.md "A read-only, forward-only result set from a query or stored procedure.")

[SADataAdapter Class](sadataadapter-class-3c15f91.md "Represents a set of commands and a database connection used to fill a System.Data.DataSet and to update a database.")

[CommandText Property](commandtext-property-3c0ed95.md "Gets or sets the text of a SQL statement or stored procedure.")

[Parameters Property](parameters-property-3c0f8d4.md "Specifies a collection of parameters for the current statement.")

