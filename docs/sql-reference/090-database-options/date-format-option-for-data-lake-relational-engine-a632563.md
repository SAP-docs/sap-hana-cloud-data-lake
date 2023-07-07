<!-- loioa632563684f2101581da9a102de30f81 -->

# DATE\_FORMAT Option for Data Lake Relational Engine

Sets the format used for dates retrieved from the database.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa632563684f2101581da9a102de30f81__section_bjc_byb_qkb"/>

## Syntax

```
DATE_FORMAT = <string_expression>
```



<a name="loioa632563684f2101581da9a102de30f81__date_format_values1"/>

## Allowed Values

String



<a name="loioa632563684f2101581da9a102de30f81__date_format_default1"/>

## Default

'YYYY-MM-DD'. This corresponds to ISO date format specifications.



<a name="loioa632563684f2101581da9a102de30f81__date_format_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.

Requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioa632563684f2101581da9a102de30f81__date_format_scope1"/>

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



<a name="loioa632563684f2101581da9a102de30f81__date_format_remarks1"/>

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

2-digit year



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

yyyy



</td>
<td valign="top" rowspan="1">

4-digit year



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mm



</td>
<td valign="top" rowspan="1">

2-digit month, or 2-digit minutes if following a colon \(as in 'hh:mm'\)



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mmm



</td>
<td valign="top" rowspan="1">

3-character name of month



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mmmm\[m...\]



</td>
<td valign="top" rowspan="1">

Character long form for months—as many characters as there are m's, until the number of m’s specified exceeds the number of characters in the month’s name



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

d



</td>
<td valign="top" rowspan="1">

Single-digit day of week, \(0 = Sunday, 6 = Saturday\)



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

dd



</td>
<td valign="top" rowspan="1">

2-digit day of month



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

ddd



</td>
<td valign="top" rowspan="1">

3-character name of the day of week



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

dddd\[d...\]



</td>
<td valign="top" rowspan="1">

Character long form for day of the week—as many characters as there are d's, until the number of d’s specified exceeds the number of characters in the day’s name



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

jjj



</td>
<td valign="top" rowspan="1">

Day of the year, from 1 to 366



</td>
</tr>
</table>

> ### Note:  
> Multibyte characters are not supported in date format strings. Only single-byte characters are allowed, even when the collation order of the database is a multibyte collation order like 932JPN. Use the concatenation operator to include multibyte characters in date format strings. For example, if '*<?\>*' represents a multibyte character, use the concatenation operator to move the multibyte character outside of the date format string:
> 
> ```
> SELECT DATEFORMAT (StartDate, 'yy') + '?'
> FROM Employees;
> ```

Each symbol is substituted with the appropriate data for the date being formatted. Any format symbol that represents character rather than digit output can be put in uppercase which causes the substituted characters to also be in uppercase. For numbers, using mixed case in the format string suppresses leading zeros.

You can control the padding of numbers by changing the case of the symbols. Same-case values \(MM, mm, DD, or dd\) all pad number with zeros. Mixed-case \(Mm, mM, Dd, or dD\) cause the number to not be zero-padded; the value takes as much room as required. For example:

```
SELECT dateformat ( cast ('2011/01/01' as date ), 'yyyy/Mm/Dd' )
```

returns this value:

```
2011/1/1
```



<a name="loioa632563684f2101581da9a102de30f81__iq_refso_455"/>

## Examples

This table illustrates DATE\_FORMAT settings, together with the output from this statement, executed on Saturday May 21, 2011:

```
SELECT CURRENT DATE
```


<table>
<tr>
<th valign="top" rowspan="1">

DATE FORMAT



</th>
<th valign="top" rowspan="1">

SELECT CURRENT DATE



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

yyyy/mm/dd/ddd



</td>
<td valign="top" rowspan="1">

2011/05/21/sat



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

jjj



</td>
<td valign="top" rowspan="1">

141



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mmm yyyy



</td>
<td valign="top" rowspan="1">

may 2011



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

mm-yyyy



</td>
<td valign="top" rowspan="1">

05-2011



</td>
</tr>
</table>

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[DATE_FORMAT Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/3e2ecb4848cc4a6ba20cd155322dee96.html "Sets the format used for dates retrieved from the database.") :arrow_upper_right:

[RETURN\_DATE\_TIME\_AS\_STRING Option for Data Lake Relational Engine](return-date-time-as-string-option-for-data-lake-relational-engine-a652ffd.md "Controls how a date, time, or timestamp value is passed to the client application when queried.")

[TIME\_FORMAT Option for Data Lake Relational Engine](time-format-option-for-data-lake-relational-engine-a664098.md "Sets the format used for times retrieved from the database.")

