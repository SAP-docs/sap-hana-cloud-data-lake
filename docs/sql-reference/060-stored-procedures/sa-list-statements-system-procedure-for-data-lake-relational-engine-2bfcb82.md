<!-- loio2bfcb827a1234d0381e210cf6bd52c93 -->

# sa\_list\_statements System Procedure for Data Lake Relational Engine

Returns the list of statements in use by the current connection.



<a name="loio2bfcb827a1234d0381e210cf6bd52c93__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_list_statements( )
```



<a name="loio2bfcb827a1234d0381e210cf6bd52c93__section_z4b_pbg_zyb"/>

## Parameters

None



## Result Set


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

handle

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

A unique handle identifying the statement.

</td>
</tr>
<tr>
<td valign="top">

statement\_number

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

num\_client\_prepares

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The number of times the client has prepared the identical statement text.The number of the statement within the connection.

</td>
</tr>
<tr>
<td valign="top">

num\_opens

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The number of times the statement has been opened.

</td>
</tr>
<tr>
<td valign="top">

schema\_version\_on\_create

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

dropped\_by\_app

</td>
<td valign="top">

BIT

</td>
<td valign="top">

The number of the statement within theIf the statement has been dropped by the client but retained for caching the value is 1; otherwise, the value is 0.

</td>
</tr>
<tr>
<td valign="top">

invalid\_cached\_statement

</td>
<td valign="top">

BIT

</td>
<td valign="top">

If this is a cached statement that is no longer valid \(for example, due to schema changes\) the value is 1; otherwise the value is 0.

</td>
</tr>
<tr>
<td valign="top">

SQLStatement

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The text of the statement.

</td>
</tr>
</table>



## Remarks

The sa\_list\_statements system procedure can be used in a CALL statement or in the FROM clause of a SELECT statement. The statement executing the sa\_list\_statements system procedure is not included in the result.

The SQLStatement column is rewritten from the original text due to semantic transform optimizations and normalization in a manner similar to that of the REWRITE function. Sensitive information such as encryption keys and passwords is replaced with \*\*\*. Because of these changes, the SQLStatement value requires interpretation when comparing to statements in the application, which might have a different form.



## Privileges

None



## Side Effects

None



## Examples

This example uses the sa\_list\_statements system procedure to return the list of statements for the connection:

```
CALL sa_list_statements();
```


<table>
<tr>
<th valign="top">

handle

</th>
<th valign="top">

statement\_number

</th>
<th valign="top">

num\_client\_prepares

</th>
<th valign="top">

num\_opens

</th>
</tr>
<tr>
<td valign="top">

196723

</td>
<td valign="top">

3

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

131098

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

65552

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="4">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

schema\_version\_on\_create

</th>
<th valign="top">

dropped\_by\_app

</th>
<th valign="top">

invalid\_cached\_statement

</th>
<th valign="top">

SQLStatement

</th>
</tr>
<tr>
<td valign="top">

1629

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

call sa\_list\_statements\(\)

</td>
</tr>
<tr>
<td valign="top">

1568

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
<td valign="top">

call sa\_ansi\_standard\_packages\('SQL:2003' 'SELECT \* \\x0D\\x0A FROM t1'\)

</td>
</tr>
<tr>
<td valign="top">

1552

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
<td valign="top">

call sp\_iqsysmon\('00:00:10'\)

</td>
</tr>
</table>

This example returns the list of statements that contribute to the max\_statement\_count resource governor:

```
SELECT *
FROM sa_list_statements()
WHERE dropped_by_app=0;
```

