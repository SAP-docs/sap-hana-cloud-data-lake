<!-- loio3c11f0fe6c5f1014a96fbfb065ea113d -->

# GetSchema\(string, string\[\]\) Method

Returns schema information for the data source of this SAConnection object and, if specified, uses the specified string for the schema name and the specified string array for the restriction values.



Visual Basic
:   ```
Public Overrides Function GetSchema (
    ByVal collection As String,
    ByVal restrictions As String()
) As DataTable
```

C\#
:   ```
public override DataTable GetSchema (
    string collection,
    string[] restrictions
)
```



## Returns

A DataTable that contains schema information.



## Remarks

These methods are used to query the database server for various metadata. Each type of metadata is given a collection name, which must be passed to receive that data. The default collection name is MetaDataCollections.

Query the .NET Data Provider to determine the list of supported schema collections by calling the GetSchema method with no arguments, or with the schema collection name *MetaDataCollections*. This will return a DataTable with a list of the supported schema collections \(CollectionName\), the number of restrictions that they each support \(NumberOfRestrictions\), and the number of identifier parts that they use \(NumberOfIdentifierParts\).


<table>
<tr>
<th valign="top">

Collection



</th>
<th valign="top">

Metadata



</th>
</tr>
<tr>
<td valign="top">

Columns



</td>
<td valign="top">

Returns information on all columns in the database.



</td>
</tr>
<tr>
<td valign="top">

DataSourceInformation



</td>
<td valign="top">

Returns information about the database server.



</td>
</tr>
<tr>
<td valign="top">

DataTypes



</td>
<td valign="top">

Returns a list of supported data types.



</td>
</tr>
<tr>
<td valign="top">

ForeignKeys



</td>
<td valign="top">

Returns information on all foreign keys in the database.



</td>
</tr>
<tr>
<td valign="top">

IndexColumns



</td>
<td valign="top">

Returns information on all index columns in the database.



</td>
</tr>
<tr>
<td valign="top">

Indexes



</td>
<td valign="top">

Returns information on all indexes in the database.



</td>
</tr>
<tr>
<td valign="top">

MetaDataCollections



</td>
<td valign="top">

Returns a list of all collection names.



</td>
</tr>
<tr>
<td valign="top">

ProcedureParameters



</td>
<td valign="top">

Returns information on all procedure parameters in the database.



</td>
</tr>
<tr>
<td valign="top">

Procedures



</td>
<td valign="top">

Returns information on all procedures in the database.



</td>
</tr>
<tr>
<td valign="top">

ReservedWords



</td>
<td valign="top">

Returns a list of reserved words used by the database server.



</td>
</tr>
<tr>
<td valign="top">

Restrictions



</td>
<td valign="top">

Returns information on restrictions used in GetSchema.



</td>
</tr>
<tr>
<td valign="top">

Tables



</td>
<td valign="top">

Returns information on all tables in the database.



</td>
</tr>
<tr>
<td valign="top">

UserDefinedTypes



</td>
<td valign="top">

Returns information on all user-defined data types in the database.



</td>
</tr>
<tr>
<td valign="top">

Users



</td>
<td valign="top">

Returns information on all users in the database.



</td>
</tr>
<tr>
<td valign="top">

ViewColumns



</td>
<td valign="top">

Returns information on all columns in views in the database.



</td>
</tr>
<tr>
<td valign="top">

Views



</td>
<td valign="top">

Returns information on all views in the database.



</td>
</tr>
</table>

These collection names are also available as read-only properties in the SAMetaDataCollectionNames class.

The results returned can be filtered by specifying an array of restrictions in the call to GetSchema.

The restrictions available with each collection can be queried by calling:

```
GetSchema( "Restrictions" )
```

If the collection requires four restrictions, then the restrictions parameter must be either NULL, or a string with four values.

To filter on a particular restriction, place the string to filter by in its place in the array and leave any unused places NULL. For example, the Tables collection has three restrictions: Owner, Table, and TableType.

To filter the Table collection by table\_name:

```
GetSchema( "Tables", new string[ ] { NULL, "my_table", NULL } )
```

This example returns information on all tables named my\_table.

```
GetSchema( "Tables", new string[ ] { "HDLADMIN", "my_table", NULL } )
```

This example returns information on all tables named my\_table owned by the user HDLADMIN.

The following list summarizes the columns returned by each collection. If the number of rows returned in a collection can be reduced by specifying a restriction on a column, then the restriction name for that column is shown in parentheses. The order in which restrictions are specified is the order in which they are presented in the lists below.

 *Columns* collection

-   TABLE\_SCHEMA \(Owner\)
-   TABLE\_NAME \(Table\)
-   COLUMN\_NAME \(Column\)
-   ORDINAL\_POSITION
-   DATA\_TYPE
-   COLUMN\_DEFAULT
-   IS\_NULLABLE
-   NUMERIC\_PRECISION
-   NUMERIC\_SCALE
-   CHARACTER\_MAXIMUM\_LENGTH
-   DATETIME\_PRECISION

 *DataSourceInformation* collection

-   CompositeIdentifierSeparatorPattern
-   DataSourceProductName
-   DataSourceProductVersion
-   DataSourceProductVersionNormalized
-   GroupByBehavior
-   IdentifierPattern
-   IdentifierCase
-   OrderByColumnsInSelect
-   ParameterMarkerFormat
-   ParameterMarkerPattern
-   ParameterNameMaxLength
-   ParameterNamePattern
-   QuotedIdentifierPattern
-   QuotedIdentifierCase
-   StatementSeparatorPattern
-   StringLiteralPattern
-   SupportedJoinOperators

 *DataTypes* collection

-   TypeName
-   ProviderDbType
-   ColumnSize
-   CreateFormat
-   CreateParameters
-   DataType
-   IsAutoIncrementable
-   IsBestMatch
-   IsCaseSensitive
-   IsFixedLength
-   IsFixedPrecisionScale
-   IsLong
-   IsNullable
-   IsSearchable
-   IsSearchableWithLike
-   IsUnsigned
-   MaximumScale
-   MinimumScale
-   IsConcurrencyType
-   IsLiteralSupported
-   LiteralPrefix
-   LiteralSuffix

 *ForeignKeys* collection

-   TABLE\_SCHEMA \(Owner\)
-   TABLE\_NAME \(Table\)
-   COLUMN\_NAME \(Column\)

 *IndexColumns* collection

-   TABLE\_SCHEMA \(Owner\)
-   TABLE\_NAME \(Table\)
-   INDEX\_NAME \(Name\)
-   COLUMN\_NAME \(Column\)
-   ORDER

 *Indexes* collection

-   TABLE\_SCHEMA \(Owner\)
-   TABLE\_NAME \(Table\)
-   INDEX\_NAME \(Name\)
-   PRIMARY\_KEY
-   IS\_UNIQUE

 *MetaDataCollections* collection

-   CollectionName
-   NumberOfRestrictions
-   NumberOfIdentifierParts

 *ProcedureParameters* collection

-   PROCEDURE\_SCHEMA \(Owner\)
-   PROCEDURE\_NAME \(Name\)
-   PARAMETER\_NAME \(Parameter\)
-   DATA\_TYPE
-   PARAMETER\_TYPE
-   IS\_INPUT
-   IS\_OUTPUT

 *Procedures* collection

-   PROCEDURE\_SCHEMA \(Owner\)
-   PROCEDURE\_NAME \(Name\)

 *ReservedWords* collection

-   reserved\_word

 *Restrictions* collection

-   CollectionName
-   RestrictionName
-   RestrictionDefault
-   RestrictionNumber

 *Tables* collection

-   TABLE\_SCHEMA \(Owner\)
-   TABLE\_NAME \(Table\)
-   TABLE\_TYPE \(TableType\) either "BASE", "VIEW", "MAT VIEW", "LCL TEMP", "GBL TEMP", "TEXT", or "TEXT GBL TEMP"

 *UserDefinedTypes* collection

-   DATA\_TYPE
-   DEFAULT
-   PRECISION
-   SCALE

 *Users* collection

-   USER\_NAME \(UserName\)
-   RESOURCE\_AUTH
-   DATABASE\_AUTH
-   SCHEDULE\_AUTH
-   USER\_GROUP

 *ViewColumns* collection

-   VIEW\_SCHEMA \(Owner\)
-   VIEW\_NAME \(Name\)
-   COLUMN\_NAME \(Column\)

 *Views* collection

-   VIEW\_SCHEMA \(Owner\)
-   VIEW\_NAME \(Name\)

**Related Information**  


[SAConnection Class](saconnection-class-3c126bb.md "Represents a connection to a database.")

