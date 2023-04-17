<!-- loio2bfcb827a1234d0381e210cf6bd52c93 -->

# sa\_list\_statements System Procedure for Data Lake Relational Engine

Returns the list of statements in use by the current connection.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_list_statements( )
```



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



The following example returns the list of statements for the connection:

```
CALL sa_list_statements();
```

The following example returns the list of statements that contribute to the max\_statement\_count resource governor:

```
SELECT *
FROM sa_list_statements()
WHERE dropped_by_app=0;
```

