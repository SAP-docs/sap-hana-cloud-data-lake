<!-- loio054a74ba291840e7bb01d3bc9588f1a2 -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_RETRY\_INTERVAL Option for Data Lake Relational Engine

Controls the amount of time \(in seconds\) to wait before a failed refresh request is requeued by the materialized view auto refresh manager.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio054a74ba291840e7bb01d3bc9588f1a2__mv_auto_refresh_interval_syntax1"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_RETRY_INTERVAL = <value>
```



<a name="loio054a74ba291840e7bb01d3bc9588f1a2__mv_auto_refresh_interval_values1"/>

## Allowed Values

Integer, in seconds. Lower limit is 0 with no upper limit.



<a name="loio054a74ba291840e7bb01d3bc9588f1a2__mv_auto_refresh_interval_default1"/>

## Default

3



<a name="loio054a74ba291840e7bb01d3bc9588f1a2__mv_auto_refresh_interval_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio054a74ba291840e7bb01d3bc9588f1a2__mv_auto_refresh_interval_scope1"/>

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

No



</td>
<td valign="top">

No



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

No



</td>
<td valign="top">

No



</td>
</tr>
</table>

**Related Information**  


[MATERIALIZED_VIEW_AUTO_REFRESH_RETRY_INTERVAL Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/01b1d2db6b4441a2a33b49e83e17187e.html "Controls the amount of time (in seconds) to wait before a failed refresh request is requeued by the materialized view auto refresh manager.") :arrow_upper_right:

