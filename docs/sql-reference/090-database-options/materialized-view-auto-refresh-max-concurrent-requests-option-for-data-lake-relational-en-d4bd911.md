<!-- loiod4bd911e17014fa7be4c4719c5cb638b -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_MAX\_CONCURRENT\_REQUESTS Option for Data Lake Relational Engine

Controls the maximum number of materialized view refresh requests that can be concurrently running in data lake Relational Engine.



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__section_cln_zxd_qrb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__mv_auto_refresh_concurrent_syntax1"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_MAX_CONCURRENT_REQUESTS = <value>;
```



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__mv_auto_refresh_concurrent_values1"/>

## Allowed Values

Integer, lower limit is 0 with no upper limit.



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__mv_auto_refresh_concurrent_default1"/>

## Default

10



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__mv_auto_refresh_concurrent_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__mv_auto_refresh_concurrent_scope1"/>

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



<a name="loiod4bd911e17014fa7be4c4719c5cb638b__mv_auto_refresh_concurrent_remarks1"/>

## Remarks

Once the limit is reached, refresh requests will be queued and will remain queued until the number of concurrent requests decreases below the limit.

**Related Information**  


[MATERIALIZED_VIEW_AUTO_REFRESH_MAX_CONCURRENT_REQUESTS Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/18ef1dc498014c8387888ec6f61220bf.html "Controls the maximum number of materialized view refresh requests that can be concurrently running in data lake Relational Engine.") :arrow_upper_right:

