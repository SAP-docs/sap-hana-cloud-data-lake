<!-- loio3c106bb06c5f1014ab01f7985dfcc8fb -->

# GetSchemaTable\(DbCommand\) Method

Returns the schema table for the SACommandBuilder object.



Visual Basic
:   ```
Protected Overrides Function GetSchemaTable (ByVal sourceCommand As DbCommand) As DataTable
```

C\#
:   ```
protected override DataTable GetSchemaTable (DbCommand sourceCommand)
```



## Parameters

sourceCommand
:   The System.Data.Common.DbCommand for which to retrieve the corresponding schema table.



## Returns

A System.Data.DataTable that represents the schema for the specific System.Data.Common.DbCommand.

**Related Information**  


[SACommandBuilder Class](sacommandbuilder-class-3c10cc1.md "A way to generate single-table SQL statements that reconcile changes made to a DataSet with the data in the associated database.")

