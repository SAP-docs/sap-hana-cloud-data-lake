<!-- loioa23b640df2c44dfa96a2ffe08faf9496 -->

# Data Type Compatibility with SAP HANA Database for CREATE EXISTING TABLE Statement in Data Lake Relational Engine

The data lake Relational Engine CREATE EXISTING TABLE statement creates a proxy table in data lake Relational Engine that points to a table in SAP HANA database.



Some data types in SAP HANA database and data lake Relational Engine are handled differently or are incompatible. When creating a data lake Relational Engine proxy table that points to an SAP HANA database physical table, it is SAP HANA database that determines compatibility.

For example, if the data lake Relational Engine proxy table points to a column in an SAP HANA database physical table with a SECONDDATE data type, the data type in the corresponding column in the data lake Relational Engine proxy table is converted to TIMESTAMP. If the data lake Relational Engine proxy table points to a column in an SAP HANA database physical table with an ARRAY, the creation of the data lake Relational Engine proxy table fails because data lake Relational Engine does not support the ARRAY data type.


<table>
<tr>
<th valign="top">

Data Type Classification



</th>
<th valign="top">

SAP HANA Database Data Type



</th>
<th valign="top">

Supports a Matching Data Type in Data Lake Relational Engine Virtual Tables?



</th>
<th valign="top">

If No, What Data Type Is Substituted in Data Lake Relational Engine Virtual Tables?



</th>
</tr>
<tr>
<td valign="top" rowspan="3">

Binary



</td>
<td valign="top">

BLOB



</td>
<td valign="top">

No



</td>
<td valign="top">

LONG BINARY



</td>
</tr>
<tr>
<td valign="top">

VARBINARY



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

VARBINARY\(*<n\>*\)



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

No



</td>
<td valign="top">

BIT



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Character



</td>
<td valign="top">

CLOB



</td>
<td valign="top">

No



</td>
<td valign="top">

LONG NVARCHAR



</td>
</tr>
<tr>
<td valign="top">

NCLOB



</td>
<td valign="top">

No



</td>
<td valign="top">

LONG NVARCHAR



</td>
</tr>
<tr>
<td valign="top">

NVARCHAR and its alias VARCHAR



</td>
<td valign="top">

No



</td>
<td valign="top">

VARCHAR \(n CHAR\)



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Datetime



</td>
<td valign="top">

DATE



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

SECONDDATE



</td>
<td valign="top">

 



</td>
<td valign="top">

DATETIMEX



</td>
</tr>
<tr>
<td valign="top">

TIME



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A

Data Lake Relational Engine supports 6 or 7 digit precision, depending on the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option and the configuration of the instance. Ensure that your instance is configured for 7 digit precision to avoid potential data loss when creating Data Lake Relational Engine proxy tables containing the TIMESTAMP data type.

For more information, see [Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine](../020-sql-data-types/decimal-precision-of-the-timestamp-data-type-in-data-lake-relational-engine-520ce6c.md).



</td>
</tr>
<tr>
<td valign="top" rowspan="9">

Numeric



</td>
<td valign="top">

SMALLDECIMAL



</td>
<td valign="top">

No



</td>
<td valign="top">

DECIMAL



</td>
</tr>
<tr>
<td valign="top">

BIGINT



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

DECIMAL and DECIMAL\(*<p\>*,*<s\>*\)



</td>
<td valign="top">

No - DECIMAL with no precision

Yes - DECIMAL with precision



</td>
<td valign="top">

DECIMAL with no precision and scale is not supported.



</td>
</tr>
<tr>
<td valign="top">

REAL



</td>
<td valign="top">

No



</td>
<td valign="top">

FLOAT



</td>
</tr>
<tr>
<td valign="top">

FLOAT



</td>
<td valign="top">

No



</td>
<td valign="top">

DOUBLE



</td>
</tr>
<tr>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

TINYINT



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top">

INTEGER or INT



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Other



</td>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

No



</td>
<td valign="top">

Not supported



</td>
</tr>
<tr>
<td valign="top">

ST\_GEOMETRY



</td>
<td valign="top">

No



</td>
<td valign="top">

Not supported



</td>
</tr>
<tr>
<td valign="top">

ST\_POINT



</td>
<td valign="top">

No



</td>
<td valign="top">

Not supported



</td>
</tr>
<tr>
<td valign="top">

ARRAY



</td>
<td valign="top">

No



</td>
<td valign="top">

Not supported



</td>
</tr>
</table>

