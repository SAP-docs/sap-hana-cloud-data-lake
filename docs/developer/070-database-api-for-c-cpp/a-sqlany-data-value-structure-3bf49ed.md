<!-- loio3bf49ed96c5f10149d94df242913c392 -->

# a\_sqlany\_data\_value Structure

Returns a description of the attributes of a data value.



```
typedef struct a_sqlany_data_value
```



## Members

All members of a\_sqlany\_data\_value, including inherited members.

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

buffer



</td>
<td valign="top">

A pointer to user supplied buffer of data.



</td>
</tr>
<tr>
<td valign="top">

public size\_t



</td>
<td valign="top">

buffer\_size



</td>
<td valign="top">

The size of the buffer.



</td>
</tr>
<tr>
<td valign="top">

public size\_t \*



</td>
<td valign="top">

length



</td>
<td valign="top">

A pointer to the number of valid bytes in the buffer. This value must be less than buffer\_size.



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

The type of the data.



</td>
</tr>
<tr>
<td valign="top">

public sacapi\_bool \*



</td>
<td valign="top">

is\_null



</td>
<td valign="top">

A pointer to indicate whether the last fetched data is NULL.



</td>
</tr>
<tr>
<td valign="top">

public sacapi\_bool



</td>
<td valign="top">

is\_address



</td>
<td valign="top">

Indicates whether the buffer value is an pointer to the actual value.



</td>
</tr>
</table>



## Remarks

To view examples of the a\_sqlany\_data\_value structure in use, see any of the following sample files in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

-   dbcapi\_isql.cpp
-   fetching\_a\_result\_set.cpp
-   send\_retrieve\_full\_blob.cpp
-   preparing\_statements.cpp

