<!-- loioa4fabf2584f21015a9d8c032cbfdc9a7 -->

# Comparison Conditions

Comparison conditions in search conditions use a comparison operator.



The syntax for comparison conditions is as follows, where *<compare\>* is a comparison operator:

```
<expression> <compare> <expression>
```

This table lists the comparison operators available in data lake Relational Engine.


<table>
<tr>
<th valign="top">

Operator

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`=`

</td>
<td valign="top">

Equal to

</td>
</tr>
<tr>
<td valign="top">

`>`

</td>
<td valign="top">

Greater than

</td>
</tr>
<tr>
<td valign="top">

`<`

</td>
<td valign="top">

Less than

</td>
</tr>
<tr>
<td valign="top">

`>=`

</td>
<td valign="top">

Greater than or equal to

</td>
</tr>
<tr>
<td valign="top">

`<=`

</td>
<td valign="top">

Less than or equal to

</td>
</tr>
<tr>
<td valign="top">

`!=`

</td>
<td valign="top">

Not equal to

</td>
</tr>
<tr>
<td valign="top">

`<>`

</td>
<td valign="top">

Not equal to

</td>
</tr>
<tr>
<td valign="top">

`!>`

</td>
<td valign="top">

Not greater than

</td>
</tr>
<tr>
<td valign="top">

`!<`

</td>
<td valign="top">

Not less than

</td>
</tr>
</table>



<a name="loioa4fabf2584f21015a9d8c032cbfdc9a7__iq_refbb_79"/>

## Example

For example, the following query retrieves the names and birth years of the oldest employees:

```
SELECT Surname, BirthDate 
FROM Employees 
WHERE Surname <= ALL (SELECT MIN(BirthDate) FROM Employees);
```

The subqueries that provide comparison values for quantified comparison predicates, as in the preceding example, might retrieve multiple rows but can only have one column.

> ### Note:  
> All string comparisons are:
> 
> -   Case-sensitive if the database was created as case respect \(the default\)
> -   Case-insensitive if the database was created as case ignore



<a name="loioa4fabf2584f21015a9d8c032cbfdc9a7__iq_refbb_80"/>

## Compatibility

-   Trailing blanks – any trailing blanks in character data are ignored for comparison purposes by SAP Adaptive Server Enterprise. The behavior of data lake Relational Engine when comparing strings is controlled by the Ignore Trailing Blanks in String Comparisons database creation option.
-   Case sensitivity – by default, data lake Relational Engine databases, like SAP ASE databases, are created as case-sensitive. Comparisons are carried out with the same attention to case as the database they are operating on. You can control the case sensitivity of data lake Relational Engine databases when creating the database.

**Related Information**  


[SQL Operators in Data Lake Relational Engine](sql-operators-in-data-lake-relational-engine-a4f0a69.md "These topics describe the arithmetic, string, and bitwise operators available in data lake Relational Engine.")

[Subqueries in Search Conditions](subqueries-in-search-conditions-a4fb435.md "A subquery is a SELECT statement enclosed in parentheses. Such a SELECT statement must contain one and only one select list item.")

[Expressions in Data Lake Relational Engine](expressions-in-data-lake-relational-engine-a4ee102.md "Expressions are formed from different kinds of elements, such as constants, column names, SQL operators, and subqueries.")

[NULL Value in Data Lake Relational Engine](null-value-in-data-lake-relational-engine-a5107a2.md "Use NULL to specify a value that is unknown, missing, or not applicable.")

[Search Conditions in Data Lake Relational Engine](search-conditions-in-data-lake-relational-engine-a4fa3d9.md "Conditions are used to choose a subset of the rows from a table, or in a control statement such as an IF statement to determine control of flow.")

[Strings in Data Lake Relational Engine](strings-in-data-lake-relational-engine-a4ed4ed.md "Strings are either literal strings, or expressions with CHAR or VARCHAR data types.")

[Three-Valued Logic](three-valued-logic-a501bc6.md "The AND, OR, NOT, and IS logical operators of SQL work in three-valued logic.")

