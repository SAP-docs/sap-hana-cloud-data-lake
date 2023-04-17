<!-- loioa501bc6584f21015a0cfba5d035e295b -->

# Three-Valued Logic

The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.



These tables show the three-valued logic.



<a name="loioa501bc6584f21015a0cfba5d035e295b__iq_refbb_109"/>

## AND Operator


<table>
<tr>
<th valign="top" rowspan="1">

AND



</th>
<th valign="top" rowspan="1">

TRUE



</th>
<th valign="top" rowspan="1">

FALSE



</th>
<th valign="top" rowspan="1">

UNKNOWN



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
</tr>
</table>



<a name="loioa501bc6584f21015a0cfba5d035e295b__iq_refbb_110"/>

## OR Operator


<table>
<tr>
<th valign="top" rowspan="1">

OR



</th>
<th valign="top" rowspan="1">

TRUE



</th>
<th valign="top" rowspan="1">

FALSE



</th>
<th valign="top" rowspan="1">

UNKNOWN



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
</tr>
</table>



<a name="loioa501bc6584f21015a0cfba5d035e295b__iq_refbb_111"/>

## NOT Operator


<table>
<tr>
<th valign="top" rowspan="1">

TRUE



</th>
<th valign="top" rowspan="1">

FALSE



</th>
<th valign="top" rowspan="1">

UNKNOWN



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

UNKNOWN



</td>
</tr>
</table>



<a name="loioa501bc6584f21015a0cfba5d035e295b__iq_refbb_112"/>

## IS Operator


<table>
<tr>
<th valign="top" rowspan="1">

IS



</th>
<th valign="top" rowspan="1">

TRUE



</th>
<th valign="top" rowspan="1">

FALSE



</th>
<th valign="top" rowspan="1">

UNKNOWN



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

UNKNOWN



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

FALSE



</td>
<td valign="top" rowspan="1">

TRUE



</td>
</tr>
</table>

**Related Information**  


[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Subqueries in Search Conditions](subqueries-in-search-conditions-a4fb435.md "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.")

[Comparison Conditions](comparison-conditions-a4fabf2.md "Comparison conditions in search conditions use a comparison operator.")

[Expressions in Data Lake Relational Engine](expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[Search Conditions in Data Lake Relational Engine](search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Strings in Data Lake Relational Engine](strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

