<!-- loiof444eb30bf634e93a0e63edb1a85ffa8 -->

# MATERIALIZED\_VIEW\_STALENESS\_LIMIT Option for Data Lake Relational Engine

Controls the maximum stale time limit, in the specified units of time.



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__section_nnn_jnr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_synatx1"/>

## Syntax

```
MATERIALIZED_VIEW_STALENESS_LIMIT = { Fresh | N { Minute[s] | Hour[s] | Day[s] | Week[s] | Month[s] } }
```



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_allowed1"/>

## Allowed Values

N is an integer greater than 0 where:

1 week = 7 days

1 month = 30 days.

Fresh = All stale reads return an error.



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_default1"/>

## Default

30 minutes



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_scope1"/>

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



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_remarks1"/>

## Remarks

This option is not supported if MATERIALIZED\_VIEW\_STALENESS\_CHECK is set to 0 \(OFF\).



<a name="loiof444eb30bf634e93a0e63edb1a85ffa8__mv_auto_refresh_staleness_limit_example1"/>

## Example

This example sets the staleness check to 30 minutes.

```
SET TEMPORARY OPTION materialized_view_staleness_limit='30 Minutes';
```

**Related Information**  


[MATERIALIZED_VIEW_STALENESS_LIMIT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/7ac82c4f1cfb46bbb18966f957d91b3d.html "Controls the maximum stale time limit, in the specified units of time.") :arrow_upper_right:

