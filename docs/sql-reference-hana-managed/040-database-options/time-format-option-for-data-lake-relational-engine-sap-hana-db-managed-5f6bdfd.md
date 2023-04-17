<!-- loio5f6bdfd6129d4e11a738e9f2909c7b3f -->

# TIME\_FORMAT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Sets the format used for times retrieved from the database.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio5f6bdfd6129d4e11a738e9f2909c7b3f__section_zd3_yc3_mrb"/>

## Syntax

```
TIME_FORMAT = <string>
```



<a name="loio5f6bdfd6129d4e11a738e9f2909c7b3f__section_f4s_yc3_mrb"/>

## Allowed values

A string composed of the symbols HH, NN, MM, SS, separated by colons.



<a name="loio5f6bdfd6129d4e11a738e9f2909c7b3f__section_jff_zc3_mrb"/>

## Default

-   'HH:NN:SS.SSS'

-   For Open Client and JDBC connections, the default is also set to HH:NN:SS.SSS.




<a name="loio5f6bdfd6129d4e11a738e9f2909c7b3f__section_kwt_yvc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio5f6bdfd6129d4e11a738e9f2909c7b3f__section_osk_1d3_mrb"/>

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



<a name="loio5f6bdfd6129d4e11a738e9f2909c7b3f__section_khc_bd3_mrb"/>

## Remarks

The format is a string using these symbols:

-   hh – two-digit hours \(24 hour clock\).
-   nn – two-digit minutes.
-   mm – two-digit minutes if following a colon \(as in 'hh:mm'\).
-   ss\[.s...s\] – two-digit seconds plus optional fraction.

Each symbol is substituted with the appropriate data for the date being formatted. Any format symbol that represents character rather than digit output can be in uppercase, which causes the substituted characters also to be in uppercase. For numbers, using mixed case in the format string suppresses leading zeros.

Multibyte characters are not supported in format strings. Only single-byte characters are allowed, even when the collation order of the database is a multibyte collation order like 932JPN.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TIME_FORMAT Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a664098384f21015ae52f7395391a59c.html "Sets the format used for times retrieved from the database.") :arrow_upper_right:

