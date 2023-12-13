<!-- loioa661dc2484f21015922195e4b2ab3b55 -->

# TEMP\_EXTRACT\_SWAP Option for Data Lake Relational Engine

In combination with the TEMP\_EXTRACT\_BINARY option, specifies the type of extraction performed by the data extraction facility.



<a name="loioa661dc2484f21015922195e4b2ab3b55__section_bgv_ksr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa661dc2484f21015922195e4b2ab3b55__section_r5n_1qh_mrb"/>

## Syntax

```
TEMP_EXTRACT_SWAP = { ON | OFF };
```



<a name="loioa661dc2484f21015922195e4b2ab3b55__iq_refso_1037"/>

## Allowed values

ON, OFF



<a name="loioa661dc2484f21015922195e4b2ab3b55__iq_refso_1038"/>

## Default

OFF



<a name="loioa661dc2484f21015922195e4b2ab3b55__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa661dc2484f21015922195e4b2ab3b55__iq_refso_1039"/>

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



<a name="loioa661dc2484f21015922195e4b2ab3b55__iq_refso_1040"/>

## Remarks

Use this option with the TEMP\_EXTRACT\_BINARY option to specify the type of extraction performed by the data extraction facility.


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

[TEMP\_EXTRACT\_BINARY Option for Data Lake Relational Engine](temp-extract-binary-option-for-data-lake-relational-engine-a65bc23.md "In combination with the TEMP_EXTRACT_SWAP option, specifies the type of extraction performed by the data extraction facility.")

