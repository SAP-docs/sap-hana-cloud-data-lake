<!-- loio3be7fe0b6c5f10149f74d1df7300ba44 -->

# SYSDOMAIN System View for Data Lake Relational Engine

The SYSDOMAIN system view records information about built-in data types \(also called domains\). The contents of this view does not change during normal operation. The underlying system table for this view is ISYSDOMAIN.



<a name="loio3be7fe0b6c5f10149f74d1df7300ba44__section_bg3_c2q_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

domain\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The unique number assigned to each data type. These numbers cannot be changed.

</td>
</tr>
<tr>
<td valign="top">

domain\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the data type normally found in the CREATE TABLE command, such as CHAR or INTEGER.

</td>
</tr>
<tr>
<td valign="top">

type\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The ODBC data type. This value corresponds to the value for data\_type in the Transact-SQL compatibility SYSTYPES table.

</td>
</tr>
<tr>
<td valign="top">

"precision"

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The number of significant digits that can be stored using this data type. The column value is NULL for non-numeric data types.

</td>
</tr>
</table>

**Related Information**  


[SYSDOMAIN System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/6fc892a4edc44df8a31252f36cb1c8d9.html "The SYSDOMAIN system view records information about built-in data types (also called domains). The contents of this view does not change during normal operation. The underlying system table for this view is ISYSDOMAIN.") :arrow_upper_right:

