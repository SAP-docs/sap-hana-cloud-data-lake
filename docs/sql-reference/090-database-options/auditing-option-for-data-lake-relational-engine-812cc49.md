<!-- loio812cc49c6ce21014a5f195897313e166 -->

# AUDITING Option for Data Lake Relational Engine

Enables and disables auditing in the database.



<a name="loio812cc49c6ce21014a5f195897313e166__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio812cc49c6ce21014a5f195897313e166__audit_syntax1"/>

## Syntax

```
AUDITING = { ON | OFF };
```



<a name="loio812cc49c6ce21014a5f195897313e166__auditing_allowed1"/>

## Allowed Values

ON, OFF



<a name="loio812cc49c6ce21014a5f195897313e166__auditing_default1"/>

## Default

OFF



<a name="loio812cc49c6ce21014a5f195897313e166__auditing_priv1"/>

## Privileges

Privilege Category: SECURITY



### 

Requires all of:

-   MANAGE AUDITING system privilege
-   SET ANY CUSTOMER SECURITY OPTION system privilege



<a name="loio812cc49c6ce21014a5f195897313e166__auditing_scope1"/>

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

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio812cc49c6ce21014a5f195897313e166__auditing_remarks1"/>

## Remarks

Auditing is the recording of details about many database events to the file container. Databases with auditing on can’t be started in read-only mode. If you require auditing for a larger set of auditing types than available in the SA\_ENABLE\_AUDITING\_TYPE system procedure, consider creating trace sessions instead.

For the AUDITING option to work, you must set the auditing option to ON, and use the SA\_ENABLE\_AUDITING\_TYPE system procedure to indicate the types of information to audit, including any combination of permission checks, connection attempts, DDL statements, public options, triggers. Auditing won’t take place if either of these conditions is true:

-   The AUDITING option is set to OFF
-   Auditing options have been disabled.

If you set the AUDITING option to ON, and don’t specify auditing options, all types of auditing information are recorded.



## Example

The following statement turns on auditing for the database.

```
SET OPTION PUBLIC.auditing = 'On';
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[AUDITING Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/05093562ca224fc2a9bbd3d9d587362c.html "Enables and disables auditing in the database.") :arrow_upper_right:

[Auditing Database Events](https://help.sap.com/viewer/a89a0a8384f21015b1e7adbeca456f73/2024_3_QRC/en-US/4c20fb59d0e848e09ffb191c9d2c0b16.html "Auditing tracks all of the activity performed on a data lake Relational Engine database.") :arrow_upper_right:

