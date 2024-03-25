<!-- loio742c50f6746f4fb488ed6498e203def4 -->

# CONCISE\_AUDITING Option for Data Lake Relational Engine

Controls whether concise auditing or legacy auditing is used.



<a name="loio742c50f6746f4fb488ed6498e203def4__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio742c50f6746f4fb488ed6498e203def4__CONCISE_AUDITING_Option_syntax1"/>

## Syntax

```
CONCISE_AUDITING  = ON|OFF;
```



<a name="loio742c50f6746f4fb488ed6498e203def4__CONCISE_AUDITING_Option_allowed_values1"/>

## Allowed Values

ON, OFF



<a name="loio742c50f6746f4fb488ed6498e203def4__CONCISE_AUDITING_Option_default1"/>

## Default

ON



<a name="loio742c50f6746f4fb488ed6498e203def4__CONCISE_AUDITING_Option_privileges1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio742c50f6746f4fb488ed6498e203def4__CONCISE_AUDITING_Option_scope1"/>

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



<a name="loio742c50f6746f4fb488ed6498e203def4__CONCISE_AUDITING_Option_remarks1"/>

## Remarks

An instance restart is required if you change the option.

Concise auditing behavior was introduced in QRC 1/2024. Setting this option to OFF reverts to legacy auditing behavior, which is deprecated.

**Related Information**  


[Auditing Database Events](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_1_QRC/en-US/4c20fb59d0e848e09ffb191c9d2c0b16.html "Auditing tracks all of the activity performed on a data lake Relational Engine database.") :arrow_upper_right:

[CONCISE_AUDITING Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/e47cf784a3274b41bbaaa416bcc07d97.html "Controls whether concise auditing or legacy auditing is used.") :arrow_upper_right:

