<!-- loioa65bc23384f210159fb68e64b1d9ab08 -->

# TEMP\_EXTRACT\_BINARY Option for Data Lake Relational Engine

In combination with the TEMP\_EXTRACT\_SWAP option, specifies the type of extraction performed by the data extraction facility.



<a name="loioa65bc23384f210159fb68e64b1d9ab08__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65bc23384f210159fb68e64b1d9ab08__section_h23_fqh_mrb"/>

## Syntax

```
TEMP_EXTRACT_BINARY = { ON | OFF };
```



<a name="loioa65bc23384f210159fb68e64b1d9ab08__iq_refso_987"/>

## Allowed Values

ON, OFF



<a name="loioa65bc23384f210159fb68e64b1d9ab08__iq_refso_988"/>

## Default

OFF



<a name="loioa65bc23384f210159fb68e64b1d9ab08__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65bc23384f210159fb68e64b1d9ab08__iq_refso_989"/>

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



<a name="loioa65bc23384f210159fb68e64b1d9ab08__iq_refso_990"/>

## Remarks

Use this option with the TEMP\_EXTRACT\_SWAP option to specify the type of extraction performed by the data extraction facility.


<table>
<tr>
<th valign="top" rowspan="1">

Extraction type

</th>
<th valign="top" rowspan="1">

TEMP\_EXTRACT\_BINARY

</th>
<th valign="top" rowspan="1">

TEMP\_EXTRACT\_SWAP

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

binary

</td>
<td valign="top" rowspan="1">

ON

</td>
<td valign="top" rowspan="1">

OFF

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

binary/swap

</td>
<td valign="top" rowspan="1">

ON

</td>
<td valign="top" rowspan="1">

ON

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

ASCII

</td>
<td valign="top" rowspan="1">

OFF

</td>
<td valign="top" rowspan="1">

OFF

</td>
</tr>
</table>

The default extraction type is ASCII.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

