<!-- loio002566cefa3a43bca454142befc1cdac -->

# TIMESTAMP\_FORMAT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Sets the format used for timestamps retrieved from the database.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio002566cefa3a43bca454142befc1cdac__section_stg_kd3_mrb"/>

## Syntax

```
TIMESTAMP_FORMAT = <string>
```



<a name="loio002566cefa3a43bca454142befc1cdac__section_xpq_kd3_mrb"/>

## Allowed Values

A string composed of the symbols listed below.



<a name="loio002566cefa3a43bca454142befc1cdac__section_odf_ld3_mrb"/>

## Default

'YYYY-MM-DD HH:NN:SS.SSS'



<a name="loio002566cefa3a43bca454142befc1cdac__section_y2c_syb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio002566cefa3a43bca454142befc1cdac__section_wvf_md3_mrb"/>

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



<a name="loio002566cefa3a43bca454142befc1cdac__section_ffr_md3_mrb"/>

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


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TIME_FORMAT Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a664098384f21015ae52f7395391a59c.html "Sets the format used for times retrieved from the database.") :arrow_upper_right:

