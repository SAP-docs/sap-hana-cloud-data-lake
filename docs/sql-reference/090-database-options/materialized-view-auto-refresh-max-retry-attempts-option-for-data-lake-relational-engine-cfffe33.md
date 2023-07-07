<!-- loiocfffe33a255f4593ae3412a93b50d2ab -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_MAX\_RETRY\_ATTEMPTS Option for Data Lake Relational Engine

Controls the number of consecutive failures of the same refresh request that can occur before it is no longer requeued by the materialized view auto refresh manager.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiocfffe33a255f4593ae3412a93b50d2ab__mv_auto_refresh_retry_syntax1"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_MAX_RETRY_ATTEMPTS = <value>
```



<a name="loiocfffe33a255f4593ae3412a93b50d2ab__mv_auto_refresh_retry_values1"/>

## Allowed Values

Integer



<a name="loiocfffe33a255f4593ae3412a93b50d2ab__mv_auto_refresh_retry_default1"/>

## Default

5



<a name="loiocfffe33a255f4593ae3412a93b50d2ab__mv_auto_refresh_retry_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiocfffe33a255f4593ae3412a93b50d2ab__mv_auto_refresh_retry_scope1"/>

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



<a name="loiocfffe33a255f4593ae3412a93b50d2ab__mv_auto_refresh_retry_remarks1"/>

## Remarks

Once the limit is exceeded, the refresh request is dropped. If the AUTO materialized view that had its refresh request dropped remains stale, it is detected by the next polling request and a new refresh request for the materialized view is queued.

**Related Information**  


[MATERIALIZED_VIEW_AUTO_REFRESH_MAX_RETRY_ATTEMPTS Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/35a8282ba03846b5a1f414244a91f046.html "Controls the number of consecutive failures of the same refresh request that can occur before it is no longer requeued by the materialized view auto refresh manager.") :arrow_upper_right:

