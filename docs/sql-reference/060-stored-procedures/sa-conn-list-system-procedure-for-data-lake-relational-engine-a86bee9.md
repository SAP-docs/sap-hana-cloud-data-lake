<!-- loioa86bee9684f2101580badd42aee0402d -->

# sa\_conn\_list System Procedure for Data Lake Relational Engine

Returns a result set containing connection IDs.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_conn_list ( [ <connidparm> ] [ ,<dbidparm> ] )
```



## Parameters

 *<connidparm\>*
 :   \(Optional\) An INTEGER parameter that specifies the connection ID number.

  *<dbidparm\>*
 :   \(Optional\) An INTEGER parameter that specifies the database ID number.

 

<a name="loioa86bee9684f2101580badd42aee0402d__section_rl2_22y_mbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



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

The connection ID number.



</td>
</tr>
</table>



<a name="loioa86bee9684f2101580badd42aee0402d__section_h3v_d2y_mbb"/>

## Remarks

If *<connidparm\>* is greater than zero, then information for the supplied connection is returned. If *<connidparm\>* is less than zero, then information for the current connection is returned. If *<connidparm\>* and *<dbidparm\>* are not supplied or are NULL, then connection IDs for all connections to all databases running on the database server are returned.

If *<connidparm\>* is NULL and *<dbidparm\>* is greater than or equal to zero, then connection IDs for only that database are returned. If *<connidparm\>* is NULL and *<dbidparm\>* is less than zero, then connection IDs for just the current database are returned.



## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). You also need the MONITOR system privilege.



<a name="loioa86bee9684f2101580badd42aee0402d__section_scv_t2y_mbb"/>

## Side Effects

None



## Example

The following example uses the sa\_conn\_list system procedure to display a list of connection IDs:

```
CALL sa_conn_list( );
```


<table>
<tr>
<th valign="top">

Number



</th>
</tr>
<tr>
<td valign="top">

1,949



</td>
</tr>
<tr>
<td valign="top">

1,948



</td>
</tr>
<tr>
<td valign="top">

...



</td>
</tr>
</table>
