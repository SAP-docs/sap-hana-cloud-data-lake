<!-- loiodf33ae20802c4ee6bb901bf679648794 -->

# BIT Data Type in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Use the BIT data type for storing Boolean values.




<table>
<tr>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

BIT



</td>
<td valign="top">

Accepts values of 1, 0, or NULL. Also accepts BOOLEAN tokens TRUE, FALSE, or UNKNOWN, where UNKNOWN is a synonym of NULL.

The default nullability is NOT NULL.

Inserting any nonzero value into a BIT column stores a 1 in the column.

When converting a string to a BIT, leading and trailing spaces are removed. If the leading character is +, it's ignored. If the leading character is -, the remaining digits are interpreted as a negative number. Leading 0 characters are skipped, and the remaining characters are converted to an integer value. An error is returned if the value isn't 0 or 1.

Only the default index type is supported for BIT data.



</td>
</tr>
<tr>
<td valign="top">

BOOLEAN



</td>
<td valign="top">

BOOLEAN is a synonym of BIT, not a native data type.

The underlying data type is BIT and the default nullability is NULL.



</td>
</tr>
</table>



<a name="loiodf33ae20802c4ee6bb901bf679648794__section_pnj_dgk_nvb"/>

## Standards

 ANSI/ISO SQL Standard
 :   Vendor extension.

 