<!-- loio3c16bb536c5f10149fb18a65c7538ba5 -->

# GetSchemaTable\(\) Method

Returns a DataTable that describes the column metadata of the SADataReader.



Visual Basic
:   ```
Public Overrides Function GetSchemaTable () As DataTable
```

C\#
:   ```
public override unsafe DataTable GetSchemaTable ()
```



## Returns

A DataTable that describes the column metadata.



## Remarks

This method returns metadata about each column in the following order:


<table>
<tr>
<th valign="top">

DataTable column



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

ColumnName



</td>
<td valign="top">

The name of the column or a null reference \(Nothing in Visual Basic\) if the column has no name. If the column is aliased in the SQL query, then the alias is returned. In result sets, not all columns have names and not all column names are unique.



</td>
</tr>
<tr>
<td valign="top">

ColumnOrdinal



</td>
<td valign="top">

The ID of the column. The value is in the range \[0, FieldCount -1\].



</td>
</tr>
<tr>
<td valign="top">

ColumnSize



</td>
<td valign="top">

For sized columns, the maximum length of a value in the column. For other columns, this is the size in bytes of the data type.



</td>
</tr>
<tr>
<td valign="top">

NumericPrecision



</td>
<td valign="top">

The precision of a numeric column or DBNull if the column is not numeric.



</td>
</tr>
<tr>
<td valign="top">

NumericScale



</td>
<td valign="top">

The scale of a numeric column or DBNull if the column is not numeric.



</td>
</tr>
<tr>
<td valign="top">

IsUnique



</td>
<td valign="top">

True if the column is a non-computed unique column in the table \(BaseTableName\) it is taken from.



</td>
</tr>
<tr>
<td valign="top">

IsKey



</td>
<td valign="top">

True if the column is one of a set of columns in the result set that taken together from a unique key for the result set. The set of columns with IsKey set to true does not need to be the minimal set that uniquely identifies a row in the result set.



</td>
</tr>
<tr>
<td valign="top">

BaseServerName



</td>
<td valign="top">

The name of the database server used by the SADataReader.



</td>
</tr>
<tr>
<td valign="top">

BaseCatalogName



</td>
<td valign="top">

The name of the catalog in the database that contains the column. This value is always DBNull.



</td>
</tr>
<tr>
<td valign="top">

BaseColumnName



</td>
<td valign="top">

The original name of the column in the table BaseTableName of the database or DBNull if the column is computed or if this information cannot be determined.



</td>
</tr>
<tr>
<td valign="top">

BaseSchemaName



</td>
<td valign="top">

The name of the schema in the database that contains the column.



</td>
</tr>
<tr>
<td valign="top">

BaseTableName



</td>
<td valign="top">

The name of the table in the database that contains the column, or DBNull if column is computed or if this information cannot be determined.



</td>
</tr>
<tr>
<td valign="top">

DataType



</td>
<td valign="top">

The .NET data type that is most appropriate for this type of column.



</td>
</tr>
<tr>
<td valign="top">

AllowDBNull



</td>
<td valign="top">

True if the column is nullable; false if the column is not nullable or if this information cannot be determined.



</td>
</tr>
<tr>
<td valign="top">

ProviderType



</td>
<td valign="top">

The type of the column.



</td>
</tr>
<tr>
<td valign="top">

IsAliased



</td>
<td valign="top">

True if the column name is an alias; false if it is not an alias.



</td>
</tr>
<tr>
<td valign="top">

IsExpression



</td>
<td valign="top">

True if the column is an expression; false if it is a column value.



</td>
</tr>
<tr>
<td valign="top">

IsIdentity



</td>
<td valign="top">

True if the column is an identity column; false if it is not an identity column.



</td>
</tr>
<tr>
<td valign="top">

IsAutoIncrement



</td>
<td valign="top">

True if the column is an autoincrement or global autoincrement column; false otherwise \(or if this information cannot be determined\).



</td>
</tr>
<tr>
<td valign="top">

IsRowVersion



</td>
<td valign="top">

True if the column contains a persistent row identifier that cannot be written to, and has no meaningful value except to identify the row.



</td>
</tr>
<tr>
<td valign="top">

IsHidden



</td>
<td valign="top">

True if the column is hidden; false otherwise.



</td>
</tr>
<tr>
<td valign="top">

IsLong



</td>
<td valign="top">

True if the column is a long varchar, long nvarchar, or a long binary column; false otherwise.



</td>
</tr>
<tr>
<td valign="top">

IsReadOnly



</td>
<td valign="top">

True if the column is read-only; false if the column is modifiable or if its access cannot be determined.



</td>
</tr>
</table>

For more information about these columns, see the .NET Framework documentation for SqlDataReader.GetSchemaTable.

For more information, see "Data access and manipulation".

