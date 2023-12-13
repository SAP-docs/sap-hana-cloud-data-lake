<!-- loio62acec57c05b463ca9add28e6bf066e2 -->

# ABAP\_VARCHAR\_MODE Option for Data Lake Relational Engine

Controls whether a SQL string or expression that contains a single space is considered the same as an empty string.



<a name="loio62acec57c05b463ca9add28e6bf066e2__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio62acec57c05b463ca9add28e6bf066e2__abap_syntax1"/>

## Syntax

```
ABAP_VARCHAR_MODE = { ON | OFF };
```



<a name="loio62acec57c05b463ca9add28e6bf066e2__abap_allowed1"/>

## Allowed Values

ON, OFF



<a name="loio62acec57c05b463ca9add28e6bf066e2__abap_default"/>

## Default

OFF



<a name="loio62acec57c05b463ca9add28e6bf066e2__abap_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio62acec57c05b463ca9add28e6bf066e2__abap_scope1"/>

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

Yes

</td>
</tr>
</table>



<a name="loio62acec57c05b463ca9add28e6bf066e2__abap_remarks1"/>

## Remarks

In ABAP VARCHAR mode, a single space and an empty string are considered the same and concatenated strings are reduced from a single space to an empty string.

To insert a single space when ABAP VARCHAR mode is turned on, use CHAR\(32\) to insert the single space instead of ' '.

Because using ABAP VARCHAR mode causes semantic differences when you insert data into a table, turning on this option affects the LIKE and EQUALITY predicates.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[ABAP_VARCHAR_MODE Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/fd417eec6ec840f291da03d66ab3c773.html "Controls whether a SQL string or expression that contains a single space is considered the same as an empty string.") :arrow_upper_right:

