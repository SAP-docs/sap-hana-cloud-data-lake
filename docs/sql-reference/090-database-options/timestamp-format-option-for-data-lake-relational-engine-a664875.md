<!-- loioa664875c84f21015ab41889496f22a0b -->

# TIMESTAMP\_FORMAT Option for Data Lake Relational Engine

Sets the format used for timestamps retrieved from the database.



<a name="loioa664875c84f21015ab41889496f22a0b__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa664875c84f21015ab41889496f22a0b__timestamp_format_syntax1"/>

## Syntax

```
TIMESTAMP_FORMAT = <string>
```



<a name="loioa664875c84f21015ab41889496f22a0b__timestamp_format_values1"/>

## Allowed Values

A string composed of the symbols listed below.



<a name="loioa664875c84f21015ab41889496f22a0b__timestamp_format_default1"/>

## Default

'YYYY-MM-DD HH:NN:SS.SSS'



<a name="loioa664875c84f21015ab41889496f22a0b__timestamp_format_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa664875c84f21015ab41889496f22a0b__timestamp_format_scope1"/>

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



<a name="loioa664875c84f21015ab41889496f22a0b__timestamp_format_remarks1"/>

## Remarks

The format is a string using these symbols:


<table>
<tr>
<th valign="top" rowspan="1">

Symbol

</th>
<th valign="top" rowspan="1">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

yy

</td>
<td valign="top" rowspan="1">

2-digit year.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

yyyy

</td>
<td valign="top" rowspan="1">

4-digit year.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mm

</td>
<td valign="top" rowspan="1">

2-digit month, or two digit minutes if following a colon \(as in 'hh:mm'\).

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mmm

</td>
<td valign="top" rowspan="1">

3-character short form for name of the month of year.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mmmm\[m...\]

</td>
<td valign="top" rowspan="1">

Character long form for month name—as many characters as there are m's, until the number of m’s specified exceeds the number of characters in the month’s name.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

dd

</td>
<td valign="top" rowspan="1">

2-digit day of month.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

ddd

</td>
<td valign="top" rowspan="1">

3-character short form for name of the day of week.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

dddd\[d...\]

</td>
<td valign="top" rowspan="1">

Character long form for day name—as many characters as there are d's, until the number of d’s specified exceeds the number of characters in the day’s name.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

hh

</td>
<td valign="top" rowspan="1">

2-digit hours.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

nn

</td>
<td valign="top" rowspan="1">

2-digit minutes.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

ss.SSS

</td>
<td valign="top" rowspan="1">

Seconds \(ss\) and fractions of a second \(SSS\), up to six decimal places. Not all platforms support timestamps to a precision of six places.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

aa

</td>
<td valign="top" rowspan="1">

a.m. or p.m. \(12-hour clock\).

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

pp

</td>
<td valign="top" rowspan="1">

p.m. if needed \(12-hour clock.\)

</td>
</tr>
</table>

Each symbol is substituted with the appropriate data for the date being formatted. Any format symbol that represents character rather than digit output can be in uppercase, which causes the substituted characters also to be in uppercase. For numbers, using mixed case in the format string suppresses leading zeros.

Multibyte characters are not supported in format strings. Only single-byte characters are allowed, even when the collation order of the database is a multibyte collation order like 932JPN.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TIMESTAMP_FORMAT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/002566cefa3a43bca454142befc1cdac.html "Sets the format used for timestamps retrieved from the database.") :arrow_upper_right:

[DATE\_FORMAT Option for Data Lake Relational Engine](date-format-option-for-data-lake-relational-engine-a632563.md "Sets the format used for dates retrieved from the database.")

[RETURN\_DATE\_TIME\_AS\_STRING Option for Data Lake Relational Engine](return-date-time-as-string-option-for-data-lake-relational-engine-a652ffd.md "Controls how a date, time, or timestamp value is passed to the client application when queried.")

