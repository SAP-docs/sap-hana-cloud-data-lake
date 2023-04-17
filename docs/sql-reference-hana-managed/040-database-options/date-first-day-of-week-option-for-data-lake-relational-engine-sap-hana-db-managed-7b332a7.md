<!-- loio7b332a76259342ac974c9701abf41265 -->

# DATE\_FIRST\_DAY\_OF\_WEEK Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Determines the first day of the week.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio7b332a76259342ac974c9701abf41265__section_dmd_tc4_hrb"/>

## Syntax

```
DATE_FIRST_DAY_OF_WEEK = { 0 | 1 | 2 | 3 | 4 | 5 | 6 }
```



<a name="loio7b332a76259342ac974c9701abf41265__section_stn_tc4_hrb"/>

## Allowed Values

0 to 6



<a name="loio7b332a76259342ac974c9701abf41265__section_dk1_5c4_hrb"/>

## Default

0 \(Sunday\)



<a name="loio7b332a76259342ac974c9701abf41265__section_bgc_dzv_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio7b332a76259342ac974c9701abf41265__section_tmm_mmb_dxb"/>

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



<a name="loio7b332a76259342ac974c9701abf41265__section_ptl_vc4_hrb"/>

## Remarks

By default, Sunday is day 1, Monday is day 2, Tuesday is day 3, and so on. This option specifies which day is the first day of the week:

-   0 – Sunday
-   1 – Monday
-   2 – Tuesday
-   3 – Wednesday
-   4 – Thursday
-   5 – Friday
-   6 – Saturday

For example, if you change the value of DATE\_FIRST\_DAY\_OF\_WEEK to 3, Wednesday becomes day 1, Thursday becomes day 2, and so on. This option only affects the DOW and DATEPART functions.

The SAP SQL Anywhere option FIRST\_DAY\_OF\_WEEK performs the same function, but assigns the values 1 through 7 instead of 0 through 6. 1 stands for Monday and 7 for Sunday \(the default\).

**Related Information**  


[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[DATEPART Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../050-system-sql-functions/datepart-function-for-data-lake-relational-engine-sap-hana-db-managed-a07008d.md "Returns an integer value for the specified part of a date/time value.")

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[DOW Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../050-system-sql-functions/dow-function-for-data-lake-relational-engine-sap-hana-db-managed-aae6da5.md "Returns a number from 1 to 7 representing the day of the week of the specified date, with Sunday=1, Monday=2, and so on.")

[DATE_FIRST_DAY_OF_WEEK Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a632279984f21015b47581522c9e7a93.html "Determines the first day of the week.") :arrow_upper_right:

