<!-- loio3bf468fa6c5f1014a17c9a6faf72c35e -->

# a\_sqlany\_data\_info Structure

Returns metadata information about a column value in a result set.



```
typedef struct a_sqlany_data_info
```



## Members

All members of a\_sqlany\_data\_info, including inherited members.

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

public a\_sqlany\_data\_type



</td>
<td valign="top">

type



</td>
<td valign="top">

The type of the data in the column.



</td>
</tr>
<tr>
<td valign="top">

public sacapi\_bool



</td>
<td valign="top">

is\_null



</td>
<td valign="top">

Indicates whether the last fetched data is NULL.

This field is only valid after a successful fetch operation.



</td>
</tr>
<tr>
<td valign="top">

public size\_t



</td>
<td valign="top">

data\_size



</td>
<td valign="top">

The total number of bytes available to be fetched.

This field is only valid after a successful fetch operation.



</td>
</tr>
</table>



## Remarks

sqlany\_get\_data\_info\(\) can be used to populate this structure with information about what was last retrieved by a fetch operation.

To view an example of the a\_sqlany\_data\_info structure in use, see the following sample file in the `sdk\dbcapi\examples` directory of your SQL Anywhere installation.

**Related Information**  


[sqlany\_get\_data\_info\(a\_sqlany\_stmt \*, sacapi\_u32, a\_sqlany\_data\_info \*\) Method](sqlany-get-data-info-a-sqlany-stmt-sacapi-u32-a-sqlany-data-info-method-3bf62e4.md "Retrieves information about the fetched data at the current row.")

