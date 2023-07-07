<!-- loioaa769ea2e3b54c92a0b6b2fd1f7e44bc -->

# MATERIALIZED\_VIEW\_STALENESS\_CHECK Option for Data Lake Relational Engine

Controls which materialized views are checked for staleness.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioaa769ea2e3b54c92a0b6b2fd1f7e44bc__mv_staleness_check_syntax1"/>

## Syntax

```
MATERIALIZED_VIEW_STALENESS_CHECK= { 0 | 1 | 2)
```



<a name="loioaa769ea2e3b54c92a0b6b2fd1f7e44bc__mv_staleness_check_values1"/>

## Allowed Values

0 - \(OFF\) No materialized views are checked for staleness when they are read.

1 - \(Default\) Only AUTO REFRESH materialized views are checked for staleness when they are read.

2 - All materialized views are checked for staleness when they are read.



<a name="loioaa769ea2e3b54c92a0b6b2fd1f7e44bc__mv_staleness_check_default1"/>

## Default

1



<a name="loioaa769ea2e3b54c92a0b6b2fd1f7e44bc__mv_staleness_check_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioaa769ea2e3b54c92a0b6b2fd1f7e44bc__mv_staleness_check_scope"/>

## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC Role



</th>
<th valign="top">

For Current User



</th>
<th valign="top">

For Other Users



</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes \(current connection only\)



</td>
<td valign="top">

No



</td>
</tr>
</table>

**Related Information**  


[MATERIALIZED_VIEW_STALENESS_CHECK Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/7f412b6887e147db9f22903b91bba87d.html "Controls which materialized views are checked for staleness.") :arrow_upper_right:

