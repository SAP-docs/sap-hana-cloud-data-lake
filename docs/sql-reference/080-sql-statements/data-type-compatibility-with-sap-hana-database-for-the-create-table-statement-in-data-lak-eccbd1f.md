<!-- loioeccbd1f58cdc49ddb7c76424a7c62737 -->

# Data Type Compatibility with SAP HANA Database for the CREATE TABLE Statement in Data Lake Relational Engine

The data lake Relational Engine CREATE TABLE statement creates a table in data lake Relational Engine.



Some data types in SAP HANA database and data lake Relational Engine are handled differently or are incompatible. When creating a SAP HANA database virtual table that points to a data lake Relational Engine physical table, it is data lake Relational Engine that determines compatibility.

For example, if the SAP HANA database virtual table points to a column in an data lake Relational Engine physical table with a LONG VARCHAR data type, the data type in the corresponding column in the SAP HANA database virtual table is converted to NCLOB. If the SAP HANA database virtual table points to a column in an data lake Relational Engine physical table with a DECIMAL or NUMERIC precision greater than 38, the creation of the SAP HANA database virtual table fails because SAP HANA database does not support a DECIMAL data type with a precision greater than 38 digits.


<table>
<tr>
<th valign="top">

Data Type Classification



</th>
<th valign="top">

Data Lake Relational Engine Data Type



</th>
<th valign="top">

Supports a Matching Data Type in SAP HANA Database Virtual Tables?



</th>
<th valign="top">

If No, Then What Data Type Is Substituted in SAP HANA Database Virtual Tables?



</th>
</tr>
<tr>
<td valign="top" rowspan="6">

Binary



</td>
<td valign="top">

BINARY



</td>
<td valign="top">

No



</td>
<td valign="top">

VARBINARY



</td>
</tr>
<tr>
<td valign="top">

BLOB



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

IMAGE



</td>
<td valign="top">

No



</td>
<td valign="top">

BLOB



</td>
</tr>
<tr>
<td valign="top">

LONG BINARY



</td>
<td valign="top">

No



</td>
<td valign="top">

BLOB



</td>
</tr>
<tr>
<td valign="top">

UNIQUEIDENTIFIER



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

BIT



</td>
<td valign="top">

BIT and its synonym BOOLEAN



</td>
<td valign="top">

BIT - No

BOOLEAN - Yes



</td>
<td valign="top">

BIT is converted to BOOLEAN



</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Character



</td>
<td valign="top">

CLOB



</td>
<td valign="top">

No



</td>
<td valign="top">

NCLOB



</td>
</tr>
<tr>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

No



</td>
<td valign="top">

BLOB



</td>
</tr>
<tr>
<td valign="top">

TEXT



</td>
<td valign="top">

No



</td>
<td valign="top">

NCLOB



</td>
</tr>
<tr>
<td valign="top">

VARCHAR \(n CHAR\)



</td>
<td valign="top">

Yes



</td>
<td valign="top">

N/A



</td>
</tr>
<tr>
<td valign="top" rowspan="6">

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

DATETIME



</td>
<td valign="top">

No



</td>
<td valign="top">

TIMESTAMP



</td>
</tr>
<tr>
<td valign="top">

SMALLDATETIME



</td>
<td valign="top">

No



</td>
<td valign="top">

TIMESTAMP



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



</td>
</tr>
<tr>
<td valign="top" rowspan="11">

Numeric



</td>
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

DECIMAL and its alias NUMERIC \(*<p\>*,*<s\>*\) where precision <= 38



</td>
<td valign="top">

DECIMAL - Yes

NUMERIC - No



</td>
<td valign="top">

NUMERIC is converted to DECIMAL in SAP HANA database



</td>
</tr>
<tr>
<td valign="top">

DECIMAL and its alias NUMERIC \(*<p\>*,*<s\>*\) where precision not specified or is \> 38



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

FLOAT



</td>
<td valign="top">

No



</td>
<td valign="top">

REAL



</td>
</tr>
<tr>
<td valign="top">

INTEGER



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

MONEY



</td>
<td valign="top">

No



</td>
<td valign="top">

DECIMAL <= a precision of 4



</td>
</tr>
<tr>
<td valign="top">

REAL



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

SMALLMONEY



</td>
<td valign="top">

No



</td>
<td valign="top">

DECIMAL <= a precision of 4



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
</table>

