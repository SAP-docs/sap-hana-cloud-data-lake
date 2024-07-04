<!-- loioa6548b1c84f210159d55cfd18f663415 -->

# SIGNIFICANTDIGITSFORDOUBLEEQUALITY Option for Data Lake Relational Engine

Specifies the number of significant digits to the right of the decimal in exponential notation that are used in equality tests between two complex arithmetic expressions.



<a name="loioa6548b1c84f210159d55cfd18f663415__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6548b1c84f210159d55cfd18f663415__SIGNIFICANTDIGITSFORDOUBLEEQUALITY_syntax1"/>

## Syntax

```
SIGNIFICANTDIGITSFORDOUBLEEQUALITY = <number_expression>
```



<a name="loioa6548b1c84f210159d55cfd18f663415__SIGNIFICANTDIGITSFORDOUBLEEQUALITY_values1"/>

## Allowed Values

0 to 15



<a name="loioa6548b1c84f210159d55cfd18f663415__SIGNIFICANTDIGITSFORDOUBLEEQUALITY_default1"/>

## Default

0



<a name="loioa6548b1c84f210159d55cfd18f663415__SIGNIFICANTDIGITSFORDOUBLEEQUALITY_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6548b1c84f210159d55cfd18f663415__SIGNIFICANTDIGITSFORDOUBLEEQUALITY_scope1"/>

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



<a name="loioa6548b1c84f210159d55cfd18f663415__SIGNIFICANTDIGITSFORDOUBLEEQUALITY_remarks1"/>

## Remarks

Doubles are stored in binary \(base 2\) instead of decimal \(base 10\); this means that this setting gives the approximate number of significant decimal digits used. If set to 0, all digits are used.

For example, when SIGNIFICANTDIGITSFORDOUBLEEQUALITY is set to 12, these numbers compare as equal; when set to 13, they do not:

-   1.23456789012345
-   1.23456789012389

SIGNIFICANTDIGITSFORDOUBLEEQUALITY affects equality tests between two complex arithmetic expressions, not those done by the indexes.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SIGNIFICANTDIGITSFORDOUBLEEQUALITY Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/c76c789fc5c64cc8bcdbb0a22e3ad765.html "Specifies the number of significant digits to the right of the decimal in exponential notation that are used in equality tests between two complex arithmetic expressions.") :arrow_upper_right:

