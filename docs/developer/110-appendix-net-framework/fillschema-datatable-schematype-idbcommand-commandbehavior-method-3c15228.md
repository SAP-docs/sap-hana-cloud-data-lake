<!-- loio3c1522856c5f10148a5c9dcc299370fc -->

# FillSchema\(DataTable, SchemaType, IDbCommand, CommandBehavior\) Method

Adds a System.Data.DataTable to a System.Data.DataSet and configures the schema to match the schema in the data source.



Visual Basic
:   ```
Protected Overrides Function FillSchema (
    ByVal dataTable As DataTable,
    ByVal schemaType As SchemaType,
    ByVal command As IDbCommand,
    ByVal behavior As CommandBehavior
) As DataTable
```

C\#
:   ```
protected override DataTable FillSchema (
    DataTable dataTable,
    SchemaType schemaType,
    IDbCommand command,
    CommandBehavior behavior
)
```



## Parameters

dataTable
:   A System.Data.DataTable to fill with the schema.

schemaType
:   One of the System.Data.SchemaType values that specify how to insert the schema.

command
:   The SQL SELECT statement used to retrieve rows from the data source.

behavior
:   One of the System.Data.CommandBehavior values.



## Returns

A reference to the System.Data.DataTable object that contains the schema.



## Remarks

For more information, see System.Data.Common.DbDataAdapter.FillSchema\(System.Data.DataTable,System.Data.SchemaType\) and "Data access and manipulation".

