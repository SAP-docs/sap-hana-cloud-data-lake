<!-- loioa642956484f21015a7a0e61656a45f16 -->

# NEAREST\_CENTURY Option \[TSQL\] for Data Lake Relational Engine

Controls the interpretation of two-digit years, in string-to-date conversions.



<a name="loioa642956484f21015a7a0e61656a45f16__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa642956484f21015a7a0e61656a45f16__section_zx3_g24_hrb"/>

## Syntax

```
NEAREST_CENTURY = <value>;
```



<a name="loioa642956484f21015a7a0e61656a45f16__iq_refso_790"/>

## Allowed Values

0 to 100



<a name="loioa642956484f21015a7a0e61656a45f16__iq_refso_791"/>

## Default

50



<a name="loioa642956484f21015a7a0e61656a45f16__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa642956484f21015a7a0e61656a45f16__iq_refso_325"/>

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



<a name="loioa642956484f21015a7a0e61656a45f16__iq_refso_792"/>

## Remarks

NEAREST\_CENTURY controls the handling of two-digit years, when converting from strings to dates or timestamps.

The NEAREST\_CENTURY setting is a numeric value that acts as a rollover point. Two-digit years less than the value are converted to 20*<yy\>*, whereas years greater than or equal to the value are converted to 19*<yy\>*.

SAP Adaptive Server Enterprise and data lake Relational Engine behavior is to use the nearest century, so that if the year value *<yy\>* is less than 50, then the year is set to 20*<yy\>*.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

