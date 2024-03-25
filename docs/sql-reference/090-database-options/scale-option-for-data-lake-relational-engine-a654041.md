<!-- loioa654041684f210159fa1d3ae7163c7f7 -->

# SCALE Option for Data Lake Relational Engine

Specifies the minimum number of digits after the decimal point when an arithmetic result is truncated to the maximum PRECISION, for queries on the catalog store only.



<a name="loioa654041684f210159fa1d3ae7163c7f7__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa654041684f210159fa1d3ae7163c7f7__section_zx3_g24_hrb"/>

## Syntax

```
SCALE = <value>
```



<a name="loioa654041684f210159fa1d3ae7163c7f7__iq_refso_928"/>

## Allowed Values

Integer, with a maximum of 126.



<a name="loioa654041684f210159fa1d3ae7163c7f7__iq_refso_929"/>

## Default

38



<a name="loioa654041684f210159fa1d3ae7163c7f7__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa654041684f210159fa1d3ae7163c7f7__iq_refso_930"/>

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



<a name="loioa654041684f210159fa1d3ae7163c7f7__iq_refso_931"/>

## Remarks

This option specifies the minimum number of digits after the decimal point when an arithmetic result is truncated to the maximum PRECISION, for queries on the catalog store.

Multiplication, division, addition, subtraction, and aggregate functions may all have results that exceed the maximum precision.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[MAX\_CLIENT\_NUMERIC\_SCALE Option for Data Lake Relational Engine](max-client-numeric-scale-option-for-data-lake-relational-engine-a63dca6.md "Controls the maximum scale for numeric data sent to the client.")

[PRECISION Option for Data Lake Relational Engine](precision-option-for-data-lake-relational-engine-a648b25.md "Specifies the maximum number of digits in the result of any decimal arithmetic, for queries on the catalog store only.")

