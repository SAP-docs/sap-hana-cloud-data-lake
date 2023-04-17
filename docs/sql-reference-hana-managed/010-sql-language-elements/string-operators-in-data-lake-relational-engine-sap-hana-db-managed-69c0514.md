<!-- loio69c0514795cd46c595ac0fcf14a9c0ef -->

# String Operators in Data Lake Relational Engine \(SAP HANA DB-Managed\)

These string operators are available in data lake Relational Engine.




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

*<expression\>* || *<expression\>*



</td>
<td valign="top">

String concatenation \(two vertical bars\). If either string is the NULL value, then the string is treated as the empty string for concatenation.



</td>
</tr>
<tr>
<td valign="top">

*<expression\>* + *<expression\>*



</td>
<td valign="top">

Alternative string concatenation. When using the + concatenation operator, you must ensure the operands are explicitly set to character data types rather than relying on implicit data conversion.



</td>
</tr>
</table>

The result data type of a string concatenation operator is a LONG VARCHAR. If you use string concatenation operators in a SELECT INTO statement, then you must use CAST and set LEFT to the correct data type and size.



<a name="loio69c0514795cd46c595ac0fcf14a9c0ef__section_u3b_23l_bwb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. The || operator is the ISO/ANSI SQL string concatenation operator.


**Related Information**  


[REVERSE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../050-system-sql-functions/reverse-function-for-data-lake-relational-engine-sap-hana-db-managed-3310f4b.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

