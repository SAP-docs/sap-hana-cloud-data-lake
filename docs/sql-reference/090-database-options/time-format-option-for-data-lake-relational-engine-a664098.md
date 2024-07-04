<!-- loioa664098384f21015ae52f7395391a59c -->

# TIME\_FORMAT Option for Data Lake Relational Engine

Sets the format used for times retrieved from the database.



<a name="loioa664098384f21015ae52f7395391a59c__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa664098384f21015ae52f7395391a59c__time_format_syntax1"/>

## Syntax

```
TIME_FORMAT = <string>
```



<a name="loioa664098384f21015ae52f7395391a59c__time_format_values1"/>

## Allowed values

A string composed of the symbols HH, NN, MM, SS, separated by colons.



<a name="loioa664098384f21015ae52f7395391a59c__time_format_default1"/>

## Default

-   'HH:NN:SS.SSS'

-   For Open Client and JDBC connections, the default is also set to HH:NN:SS.SSS.




<a name="loioa664098384f21015ae52f7395391a59c__time_format_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa664098384f21015ae52f7395391a59c__time_format_scope1"/>

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



<a name="loioa664098384f21015ae52f7395391a59c__time_format_remarks1"/>

## Remarks

The format is a string using these symbols:

-   hh – two-digit hours \(24 hour clock\).
-   nn – two-digit minutes.
-   mm – two-digit minutes if following a colon \(as in 'hh:mm'\).
-   ss\[.s...s\] – two-digit seconds plus optional fraction.

Each symbol is substituted with the appropriate data for the date being formatted. Any format symbol that represents character rather than digit output can be in uppercase, which causes the substituted characters also to be in uppercase. For numbers, using mixed case in the format string suppresses leading zeros.

Multibyte characters are not supported in format strings. Only single-byte characters are allowed, even when the collation order of the database is a multibyte collation order like 932JPN.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TIME_FORMAT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/5f6bdfd6129d4e11a738e9f2909c7b3f.html "Sets the format used for times retrieved from the database.") :arrow_upper_right:

[DATE\_FORMAT Option for Data Lake Relational Engine](date-format-option-for-data-lake-relational-engine-a632563.md "Sets the format used for dates retrieved from the database.")

[RETURN\_DATE\_TIME\_AS\_STRING Option for Data Lake Relational Engine](return-date-time-as-string-option-for-data-lake-relational-engine-a652ffd.md "Controls how a date, time, or timestamp value is passed to the client application when queried.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

