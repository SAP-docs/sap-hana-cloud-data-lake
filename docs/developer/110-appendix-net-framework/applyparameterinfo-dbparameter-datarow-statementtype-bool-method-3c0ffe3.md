<!-- loio3c0ffe346c5f101487d4ceace1c334d1 -->

# ApplyParameterInfo\(DbParameter, DataRow, StatementType, bool\) Method

Allows the provider implementation of System.Data.Common.DbCommandBuilder to handle additional parameter properties.



Visual Basic
:   ```
Protected Overrides Sub ApplyParameterInfo (
    ByVal parameter As DbParameter,
    ByVal row As DataRow,
    ByVal statementType As StatementType,
    ByVal whereClause As Boolean
)
```

C\#
:   ```
protected override void ApplyParameterInfo (
    DbParameter parameter,
    DataRow row,
    StatementType statementType,
    bool whereClause
)
```



## Parameters

parameter
:   A System.Data.Common.DbParameter to which the additional modifications are applied.

row
:   The System.Data.DataRow from the schema table provided by SADataReader.GetSchemaTable.

statementType
:   The type of command being generated: INSERT, UPDATE or DELETE.

whereClause
:   The value is true if the parameter is part of the UPDATE or DELETE WHERE clause, and false if it is part of the INSERT or UPDATE values.

**Related Information**  


[GetSchemaTable\(\) Method](getschematable-method-3c16bb5.md "Returns a DataTable that describes the column metadata of the SADataReader.")

