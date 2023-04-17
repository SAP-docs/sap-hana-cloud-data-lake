<!-- loio3c108b116c5f1014a8e5f9b0be5ef189 -->

# InitializeCommand\(DbCommand\) Method

Resets the System.Data.Common.DbCommand.CommandTimeout, System.Data.Common.DbCommand.Transaction, System.Data.Common.DbCommand.CommandType, and System.Data.Common.DbCommand.UpdatedRowSource properties on the System.Data.Common.DbCommand.



Visual Basic
:   ```
Protected Overrides Function InitializeCommand (ByVal command As DbCommand) As DbCommand
```

C\#
:   ```
protected override DbCommand InitializeCommand (DbCommand command)
```



## Parameters

command
:   The System.Data.Common.DbCommand to be used by the command builder for the corresponding insert, update, or delete command.



## Returns

A System.Data.Common.DbCommand instance to use for each insert, update, or delete operation. Passing a null value allows the InitializeCommand method to create a System.Data.Common.DbCommand object based on the SELECT statement associated with the SACommandBuilder object.

**Related Information**  


[SACommandBuilder Class](sacommandbuilder-class-3c10cc1.md "A way to generate single-table SQL statements that reconcile changes made to a DataSet with the data in the associated database.")

