<!-- loioa4f1c6da84f210159f29edb6550416f1 -->

# String Operators in Data Lake Relational Engine

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



<a name="loioa4f1c6da84f210159f29edb6550416f1__string_op_section2"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant. The || operator is the ISO/ANSI SQL string concatenation operator.


**Related Information**  


[REVERSE Function \[String\] for Data Lake Relational Engine](../050-system-sql-functions/reverse-function-string-for-data-lake-relational-engine-a57a972.md "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.")

