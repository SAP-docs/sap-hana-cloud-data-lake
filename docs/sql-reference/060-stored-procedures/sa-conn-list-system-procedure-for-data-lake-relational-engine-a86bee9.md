<!-- loioa86bee9684f2101580badd42aee0402d -->

# sa\_conn\_list System Procedure for Data Lake Relational Engine

Returns a result set containing connection IDs.



<a name="loioa86bee9684f2101580badd42aee0402d__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_conn_list ( [ <connidparm> ] [ ,<dbidparm> ] )
```



## Parameters


<dl>
<dt><b>

*<connidparm\>*

</b></dt>
<dd>

\(Optional\) An INTEGER parameter that specifies the connection ID number.



</dd><dt><b>

*<dbidparm\>*

</b></dt>
<dd>

\(Optional\) An INTEGER parameter that specifies the database ID number.



</dd>
</dl>



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

Requires EXECUTE object-level privilege on this procedure. To obtain a list of all connection IDs, you also need the MONITOR system privilege.



<a name="loioa86bee9684f2101580badd42aee0402d__section_scv_t2y_mbb"/>

## Side Effects

None.



## Examples

This example returns a list of connection IDs:

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

1949

</td>
</tr>
<tr>
<td valign="top">

1948

</td>
</tr>
<tr>
<td valign="top">

...

</td>
</tr>
</table>

