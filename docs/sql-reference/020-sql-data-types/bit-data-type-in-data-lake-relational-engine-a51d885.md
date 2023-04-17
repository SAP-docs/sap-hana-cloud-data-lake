<!-- loioa51d885d84f21015a438bf3fe9f5fcf6 -->

# BIT Data Type in Data Lake Relational Engine

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



<a name="loioa51d885d84f21015a438bf3fe9f5fcf6__bit_data_type_standards"/>

## Standards

 ANSI/ISO SQL Standard
 :   Vendor extension.

 