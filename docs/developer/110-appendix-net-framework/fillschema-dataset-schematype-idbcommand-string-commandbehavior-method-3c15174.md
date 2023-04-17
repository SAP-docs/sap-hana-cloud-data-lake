<!-- loio3c1517436c5f10148f66c610e99f854a -->

# FillSchema\(DataSet, SchemaType, IDbCommand, string, CommandBehavior\) Method

Adds a System.Data.DataTable to a System.Data.DataSet and configures the schema to match the schema in the data source.



Visual Basic
:   ```
Protected Overrides Function FillSchema (
    ByVal dataSet As DataSet,
    ByVal schemaType As SchemaType,
    ByVal command As IDbCommand,
    ByVal srcTable As String,
    ByVal behavior As CommandBehavior
) As DataTable()
```

C\#
:   ```
protected override DataTable[] FillSchema (
    DataSet dataSet,
    SchemaType schemaType,
    IDbCommand command,
    string srcTable,
    CommandBehavior behavior
)
```



## Parameters

dataSet
:   A System.Data.DataSet to fill with the schema.

schemaType
:   One of the System.Data.SchemaType values that specify how to insert the schema.

command
:   The SQL SELECT statement used to retrieve rows from the data source.

srcTable
:   The name of the source table to use for table mapping.

behavior
:   One of the System.Data.CommandBehavior values.



## Returns

A reference to a collection of System.Data.DataTable objects that were added to the System.Data.DataSet.



## Remarks

For more information, see System.Data.IDataAdapter.FillSchema and "Data access and manipulation".

