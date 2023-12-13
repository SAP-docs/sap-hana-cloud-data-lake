<!-- loioa248737984f21015a82f960e9878cbd1 -->

# RESERVED\_KEYWORDS Option for Data Lake Relational Engine

Turns on individual keywords that are disabled by default.



<a name="loioa248737984f21015a82f960e9878cbd1__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_syntax1"/>

## Syntax

```
RESERVED_KEYWORDS = <string_expression>;
```



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_values1"/>

## Allowed Values

String



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_default1"/>

## Default

' ' \(the empty string\)



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_priv1"/>

## Privileges

Privilege Category: SYSTEM



### 

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_scope1"/>

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

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_remarks1"/>

## Remarks

This option turns on individual keywords that are disabled by default. Only the LIMIT keyword can be turned on.



<a name="loioa248737984f21015a82f960e9878cbd1__reserved_keywords_examples1"/>

## Examples

The following statement allows the LIMIT keyword to be recognized as a keyword:

```
SET OPTION RESERVED_KEYWORDS = 'LIMIT';
```

You cannot turn on the keywords SET, OPTION, and OPTIONS. The following determine whether a word is identified as a keyword \(in order of precedence\):

-   It appears in the SAP SQL Anywhere list of reserved words
-   It is turned on with the RESERVED\_KEYWORDS option
-   It is turned off with the NON\_KEYWORDS option

Each setting of this option replaces the previous setting. The following statement clears all previous settings:

```
SET OPTION RESERVED_KEYWORDS = ;
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[RESERVED_KEYWORDS Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/991b4fb75bed4696885132f2c32419be.html "Turns on individual keywords that are disabled by default.") :arrow_upper_right:

