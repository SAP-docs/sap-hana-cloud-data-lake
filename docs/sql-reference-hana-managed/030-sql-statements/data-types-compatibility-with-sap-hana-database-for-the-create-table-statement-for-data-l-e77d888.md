<!-- loioe77d8889ae14496881ac55495b4262ea -->

# Data Types Compatibility with SAP HANA Database for the CREATE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The data lake Relational Engine CREATE TABLE statement lets you create a data lake Relational Engine physical table.



Once the physical table is created, data lake Relational Engine automatically triggers SAP HANA database to create a corresponding virtual table that points to the original data lake Relational Engine table. In the event a data lake Relational Engine data type isn't supported in SAP HANA database, where possible, SAP HANA database automatically substitutes an equivalent SAP HANA database data type in the virtual table.

For example, the data lake Relational Engine data type DATETIME is not supported in SAP HANA database, but SAP HANA database does support the data type TIMESTAMP, which is equivalent to DATETIME. So, in the virtual table, SAP HANA database automatically substitutes TIMESTAMP for DATETIME.

In the event no equivalent data type is available, the data lake Relational Engine physical table is created, but not the SAP HANA database virtual table.

Use this table to understand the data type mappings between data lake Relational Engine and SAP HANA database when using the data lake Relational Engine CREATE TABLE statement.


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

DATETIMEX

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



<a name="loioe77d8889ae14496881ac55495b4262ea__data_types_managed2"/>

## Functional Restriction:

Native SAP HANA database data types not included in the **Supported in SAP HANA Database Virtual Tables?** column are not supported in this data lake release. Examples include CS\_ALPHANUM, and CS\_RAW.

