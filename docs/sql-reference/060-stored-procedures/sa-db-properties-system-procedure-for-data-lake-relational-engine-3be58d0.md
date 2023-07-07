<!-- loio3be58d086c5f1014925bf0cfadeb33ef -->

# sa\_db\_properties System Procedure for Data Lake Relational Engine

Reports database property information.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_db_properties( [ <dbidparm> ] )
```



## Parameters


<dl>
<dt><b>

 *<dbidparm\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the database ID number. The default is NULL.



</dd>
</dl>



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

Number



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The database ID number.



</td>
</tr>
<tr>
<td valign="top">

PropNum



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The database property number.



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

The database property name.



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

The database property description.



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

The database property value.



</td>
</tr>
</table>



## Remarks

If you specify a database ID, the sa\_db\_properties system procedure returns the database ID number and the PropNum, PropName, PropDescription, and Value for each available database property. Values are returned for all database properties and statistics related to databases. Valid properties with NULL values are also returned.

If *<dbidparm\>* is greater than zero, then database properties for the supplied database are returned. If *<dbidparm\>* is less than zero, then database properties for the current database are returned. If *<dbidparm\>* is not supplied or is NULL, then database properties for all databases running on the database server are returned.



## Privileges

Requires EXECUTE object-level privilege on the procedure.

To execute this procedure for other databases, also requires one of:

-   SERVER OPERATOR system privilege
-   MONITOR system privilege



## Side Effects

None



The following example uses the sa\_db\_properties system procedure to return a result set summarizing database properties for all databases when the invoker has SERVER OPERATOR or MONITOR system privilege. Otherwise, database properties for the current database are returned.

```
CALL sa_db_properties( );
```


<table>
<tr>
<th valign="top">

Number



</th>
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

0



</td>
<td valign="top">

0



</td>
<td valign="top">

ConnCount



</td>
<td valign="top">

...



</td>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

1



</td>
<td valign="top">

IdleCheck



</td>
<td valign="top">

...



</td>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

2



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

...



</td>
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

The following example uses the sa\_db\_properties system procedure to return a result set summarizing database properties for a second database.

```
CALL sa_db_properties( 1 );
```

