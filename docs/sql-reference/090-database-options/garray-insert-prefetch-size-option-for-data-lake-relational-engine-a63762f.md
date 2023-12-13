<!-- loioa63762f984f21015ba82ab508d88e950 -->

# GARRAY\_INSERT\_PREFETCH\_SIZE Option for Data Lake Relational Engine

Specifies number of pages used for prefetch.



<a name="loioa63762f984f21015ba82ab508d88e950__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63762f984f21015ba82ab508d88e950__section_zx3_g24_hrb"/>

## Syntax

```
GARRAY_INSERT_PREFETCH_SIZE = <value>;
```



<a name="loioa63762f984f21015ba82ab508d88e950__iq_refso_565"/>

## Allowed Values

0 to 100



<a name="loioa63762f984f21015ba82ab508d88e950__iq_refso_566"/>

## Default

3



<a name="loioa63762f984f21015ba82ab508d88e950__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63762f984f21015ba82ab508d88e950__iq_refso_567"/>

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



<a name="loioa63762f984f21015ba82ab508d88e950__iq_refso_568"/>

## Remarks

This option defines the number of database pages read ahead during an insert to a column that has an HG index.

Do not set this option unless advised to do so by Technical Support.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[GARRAY\_FILL\_FACTOR\_PERCENT Option for Data Lake Relational Engine](garray-fill-factor-percent-option-for-data-lake-relational-engine-a637325.md "Specifies the percent of space on each HG garray page to reserve for future incremental inserts into existing groups.")

