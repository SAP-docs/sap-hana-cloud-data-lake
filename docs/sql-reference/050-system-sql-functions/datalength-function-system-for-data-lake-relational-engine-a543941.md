<!-- loioa543941884f21015a485f9b55b14d889 -->

# DATALENGTH Function \[System\] for Data Lake Relational Engine

Returns the length of the expression in bytes.



```
DATALENGTH ( <expression> );
```



<a name="loioa543941884f21015a485f9b55b14d889__iq_refbb_387"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression is usually a column name. If the expression is a string constant, it must be enclosed in quotes.



</dd>
</dl>



## Result Set

UNSIGNED INT



<a name="loioa543941884f21015a485f9b55b14d889__iq_refbb_389"/>

## Remarks


<table>
<tr>
<th valign="top">

Data Type

</th>
<th valign="top">

DATALENGTH

</th>
</tr>
<tr>
<td valign="top">

SMALLINT

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

INTEGER

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

DOUBLE

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

CHAR

</td>
<td valign="top">

Length of the data

</td>
</tr>
<tr>
<td valign="top">

BINARY

</td>
<td valign="top">

Length of the data

</td>
</tr>
</table>



<a name="loioa543941884f21015a485f9b55b14d889__iq_refbb_391"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa543941884f21015a485f9b55b14d889__iq_refbb_390"/>

## Examples

Returns the value 35, the longest string in the company\_name column:

```
SELECT MAX( DATALENGTH( company_name ) )
                    FROM Customers;
```

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

