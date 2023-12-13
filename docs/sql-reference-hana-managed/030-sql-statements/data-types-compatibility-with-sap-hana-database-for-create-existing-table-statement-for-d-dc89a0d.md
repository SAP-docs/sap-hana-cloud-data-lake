<!-- loiodc89a0d48ca245ffbe940bc3d4ba9d61 -->

# Data Types Compatibility with SAP HANA Database for CREATE EXISTING TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The data lake Relational Engine CREATE EXISTING TABLE statement lets you create a data lake Relational Engine proxy table that points to an SAP HANA database physical table.



When creating the proxy table, if data lake Relational Engine does not support a data type of the SAP HANA database table, data lake Relational Engine automatically substitutes an equivalent data lake Relational Engine type that is supported. If no substitution is available, the CREATE EXISTING TABLE statement fails.



Use this table to understand the data type mappings between data lake Relational Engine and SAP HANA database when using the data lake Relational Engine CREATE EXISTING TABLE statement.




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

For more information, see [Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../020-sql-data-types/decimal-precision-of-the-timestamp-data-type-in-data-lake-relational-engine-sap-hana-db-m-5cbca14.md).

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

