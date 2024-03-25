<!-- loiobeb258e2c5044c44aebc49f3d6318ca2 -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_POLLING\_INTERVAL Option for Data Lake Relational Engine

Controls the amount of time \(in minutes\) between polling refresh requests executed by the materialized view auto refresh manager.



<a name="loiobeb258e2c5044c44aebc49f3d6318ca2__section_nnn_jnr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiobeb258e2c5044c44aebc49f3d6318ca2__mv_auto_refresh_pooling_syntax1"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_POLLING_INTERVAL  = <value>;
```



<a name="loiobeb258e2c5044c44aebc49f3d6318ca2__mv_auto_refresh_pooling_values1"/>

## Allowed Values

Integer, in minutes. Lower limit is 1 with no upper limit.



<a name="loiobeb258e2c5044c44aebc49f3d6318ca2__mv_auto_refresh_pooling_default1"/>

## Default

2



<a name="loiobeb258e2c5044c44aebc49f3d6318ca2__mv_auto_refresh_pooling_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiobeb258e2c5044c44aebc49f3d6318ca2__mv_auto_refresh_pooling_scope1"/>

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


[MATERIALIZED_VIEW_AUTO_REFRESH_POLLING_INTERVAL Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/84aa190c7a8f463196bd9755c6146a29.html "Controls the amount of time (in minutes) between polling refresh requests executed by the materialized view auto refresh manager.") :arrow_upper_right:

