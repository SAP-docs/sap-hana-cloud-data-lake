<!-- loio3be5bff46c5f10149c2c85dc65723d6e -->

# sa\_eng\_properties System Procedure for Data Lake Relational Engine

Reports database server property information.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_eng_properties( )
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

PropNum



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The database server property number.



</td>
</tr>
<tr>
<td valign="top">

PropName



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

The database server property name.



</td>
</tr>
<tr>
<td valign="top">

PropDescription



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

The database server property description.



</td>
</tr>
<tr>
<td valign="top">

Value



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The database server property value.



</td>
</tr>
</table>



## Remarks

Returns the PropNum, PropName, PropDescription, and Value for each available server property. Values are returned for all database server properties and statistics related to database servers.



## Privileges

You need to have the EXECUTE privilege on the system procedure.



## Side Effects

None



The following statement returns a set of available server properties

```
CALL sa_eng_properties( );
```


<table>
<tr>
<th valign="top">

PropNum



</th>
<th valign="top">

PropName



</th>
<th valign="top">

...



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

IdleWrite



</td>
<td valign="top">

...



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

IdleChkPt



</td>
<td valign="top">

...



</td>
</tr>
<tr>
<td valign="top">

...



</td>
<td valign="top">

...



</td>
<td valign="top">

...



</td>
</tr>
</table>

