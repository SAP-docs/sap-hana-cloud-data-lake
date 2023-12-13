<!-- loioa636102b84f21015b199ddc65fd14880 -->

# FORCE\_NO\_SCROLL\_CURSORS Option for Data Lake Relational Engine

Forces all cursors to be non-scrolling.



<a name="loioa636102b84f21015b199ddc65fd14880__section_jq1_3gr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa636102b84f21015b199ddc65fd14880__section_vn4_rzh_3rb"/>

## Syntax

```
FORCE_NO_SCROLL_CURSORS = { ON | OFF };
```



<a name="loioa636102b84f21015b199ddc65fd14880__iq_refso_532"/>

## Allowed Values

ON, OFF



<a name="loioa636102b84f21015b199ddc65fd14880__iq_refso_533"/>

## Default

OFF



<a name="loioa636102b84f21015b199ddc65fd14880__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa636102b84f21015b199ddc65fd14880__iq_refso_534"/>

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



<a name="loioa636102b84f21015b199ddc65fd14880__iq_refso_535"/>

## Remarks

By default, all cursors are scrolling. Scrolling cursors with no host variable declared cause data lake Relational Engine to create a buffer for temporary storage of results. Each row in the result set is stored to allow for backward scrolling.

Setting FORCE\_NO\_SCROLL\_CURSORS to ON reduces temporary storage requirements. This option can be useful if you are retrieving very large numbers \(millions\) of rows. However if your front-end application makes frequent use of backward-scrolling cursor operations, query response will be faster with this option set to OFF.

If your front-end application rarely performs backward-scrolling, make FORCE\_NO\_SCROLL\_CURSORS = 'ON' a permanent PUBLIC option, to use less memory and improve query performance.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

