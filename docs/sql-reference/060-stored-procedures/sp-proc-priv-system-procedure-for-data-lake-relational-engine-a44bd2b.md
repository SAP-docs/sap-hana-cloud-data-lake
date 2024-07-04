<!-- loioa44bd2bd84f21015abce97fe6b205f4d -->

# sp\_proc\_priv System Procedure for Data Lake Relational Engine

Generates a report of the minimum system privileges required to run a stored procedure and pass the privilege check for the procedure.



<a name="loioa44bd2bd84f21015abce97fe6b205f4d__section_spb_5dw_f4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_proc_priv ( [ <proc_name> ] )
```



<a name="loioa44bd2bd84f21015abce97fe6b205f4d__section_x5w_b1j_yyb"/>

## Parameters


<dl>
<dt><b>

*<proc\_name\>*

</b></dt>
<dd>

The name of the procedure.



</dd>
</dl>



<a name="loioa44bd2bd84f21015abce97fe6b205f4d__section_z4x_jqr_mbb"/>

## Remarks

If multiple system privileges, separated by a comma, are displayed for a stored procedure, this implies that any one of them would suffice to execute the stored procedure. If multiple rows are displayed for a stored procedure, then one system privilege from each row is required to execute the stored procedure.

This procedure lists only those system privileges for a stored procedure that will always pass the privilege check for the procedure. There may be other system privileges which would pass the privilege check to execute the procedure given conditions, but these are not listed by this procedure.



<a name="loioa44bd2bd84f21015abce97fe6b205f4d__section_a22_3qr_mbb"/>

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

proc\_name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the stored procedure.

</td>
</tr>
<tr>
<td valign="top">

privilege

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The privileges required to pass privilege check.

</td>
</tr>
</table>



<a name="loioa44bd2bd84f21015abce97fe6b205f4d__section_dln_stv_xyb"/>

## Remarks

If sp\_proc\_priv is invoked without any parameter specified, the procedure displays all the stored procedures and the system privileges required to execute each. Stored procedures which do not require any system privileges for their execution are not displayed.

If sp\_proc\_priv is invoked with a procedure name parameter, it returns the system privileges required to execute that procedure. If no system privileges are required, it lists "***No Privilege Required***" against the procedure.



## Privileges

Requires EXECUTE object-level privilege on this procedure.



<a name="loioa44bd2bd84f21015abce97fe6b205f4d__section_fds_zss_mbb"/>

## Side Effects

None.



## Examples

This example returns associated privileges with the stored procedure.

```
CALL sp_proc_priv ('sp_iqrowdensity');
```


<table>
<tr>
<th valign="top">

proc\_name

</th>
<th valign="top">

privileges

</th>
</tr>
<tr>
<td valign="top">

sp\_iqrowdensity

</td>
<td valign="top">

MONITOR, MANAGE ANY DBSPACE, CREATE ANY INDEX, ALTER ANY INDEX, CREATE ANY OBJECT, ALTER ANY OBJECT

</td>
</tr>
</table>

This example returns all stored procedures and the associated privileges.

```
CALL sp_proc_priv ( );
```


<table>
<tr>
<th valign="top">

proc\_name

</th>
<th valign="top">

privileges

</th>
</tr>
<tr>
<td valign="top">

sp\_iqrowdensity

</td>
<td valign="top">

MONITOR, MANAGE ANY DBSPACE, CREATE ANY INDEX, ALTER ANY INDEX, CREATE ANY OBJECT, ALTER ANY OBJECT

</td>
</tr>
<tr>
<td valign="top">

sp\_iqworkmon

</td>
<td valign="top">

MONITOR

</td>
</tr>
<tr>
<td valign="top">

sp\_iqindexsize

</td>
<td valign="top">

MANAGE ANY DBSPACE, ALTER ANY INDEX, ALTER ANY OBJECT

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

