<!-- loio3bf4465b6c5f1014b8628a543915e548 -->

# a\_sqlany\_column\_info Structure

Returns column metadata information.



```
typedef struct a_sqlany_column_info
```



## Members

All members of a\_sqlany\_column\_info, including inherited members.

 **Variables** 


<table>
<tr>
<th valign="top">

Modifier and Type



</th>
<th valign="top">

Variable



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

public char \*



</td>
<td valign="top">

name



</td>
<td valign="top">

The name of the column \(null-terminated\).

The string can be referenced as long as the result set object is not freed.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_data\_type



</td>
<td valign="top">

type



</td>
<td valign="top">

The column data type.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_native\_type



</td>
<td valign="top">

native\_type



</td>
<td valign="top">

The native type of the column in the database.



</td>
</tr>
<tr>
<td valign="top">

public unsigned short



</td>
<td valign="top">

precision



</td>
<td valign="top">

The precision.



</td>
</tr>
<tr>
<td valign="top">

public unsigned short



</td>
<td valign="top">

scale



</td>
<td valign="top">

The scale.



</td>
</tr>
<tr>
<td valign="top">

public size\_t



</td>
<td valign="top">

max\_size



</td>
<td valign="top">

The maximum size a data value in this column can take.



</td>
</tr>
<tr>
<td valign="top">

public sacapi\_bool



</td>
<td valign="top">

nullable



</td>
<td valign="top">

Indicates whether a value in the column can be null.



</td>
</tr>
<tr>
<td valign="top">

public char \*



</td>
<td valign="top">

table\_name



</td>
<td valign="top">

The name of the table \(null-terminated\).

The string can be referenced as long as the result set object is not freed.



</td>
</tr>
<tr>
<td valign="top">

public char \*



</td>
<td valign="top">

owner\_name



</td>
<td valign="top">

The name of the owner \(null-terminated\).

The string can be referenced as long as the result set object is not freed.



</td>
</tr>
<tr>
<td valign="top">

public sacapi\_bool



</td>
<td valign="top">

is\_bound



</td>
<td valign="top">

Indicates whether the column is bound to a user buffer.



</td>
</tr>
<tr>
<td valign="top">

public a\_sqlany\_data\_value



</td>
<td valign="top">

binding



</td>
<td valign="top">

Information about the bound column.



</td>
</tr>
</table>



## Remarks

sqlany\_get\_column\_info\(\) can be used to populate this structure.

To view an example of the a\_sqlany\_column\_info structure in use, see the following sample file in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

-   dbcapi\_isql.cpp

