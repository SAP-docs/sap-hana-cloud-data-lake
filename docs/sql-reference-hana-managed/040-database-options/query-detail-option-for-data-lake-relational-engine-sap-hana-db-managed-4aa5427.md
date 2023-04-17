<!-- loio4aa5427fd7c64273ae3b7d06a5c33ce8 -->

# QUERY\_DETAIL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies whether or not to include additional query information in the Query Detail section of the query plan.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio4aa5427fd7c64273ae3b7d06a5c33ce8__section_kcr_nct_lrb"/>

## Syntax

```
QUERY_DETAIL = { ON | OFF }
```



<a name="loio4aa5427fd7c64273ae3b7d06a5c33ce8__section_q21_4ct_lrb"/>

## Allowed Values

ON, OFF



<a name="loio4aa5427fd7c64273ae3b7d06a5c33ce8__section_w54_4ct_lrb"/>

## Default

ON



<a name="loio4aa5427fd7c64273ae3b7d06a5c33ce8__section_tcc_vsb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



Privilege Category: PUBLIC

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio4aa5427fd7c64273ae3b7d06a5c33ce8__section_r3y_pct_lrb"/>

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



<a name="loio4aa5427fd7c64273ae3b7d06a5c33ce8__section_pmt_qct_lrb"/>

## Remarks

When QUERY\_DETAIL and QUERY\_PLAN \(or QUERY\_PLAN\_AS\_HTML\) are both turned on, data lake Relational Engine displays additional information about the query when producing its query plan. When QUERY\_PLAN and QUERY\_PLAN\_AS\_HTML are OFF, this option is ignored.

When QUERY\_PLAN is ON \(the default\), especially if QUERY\_DETAIL is also ON, you might want to enable message log wrapping or message log archiving to avoid filling up your message log file.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_PLAN\_AS\_HTML Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](query-plan-as-html-option-for-data-lake-relational-engine-sap-hana-db-managed-486458a.md "Generates graphical query plans in HTML format for viewing in a Web browser.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[QUERY_DETAIL Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a64c3ef384f21015ac76f94d8db150c5.html "Specifies whether or not to include additional query information in the Query Detail section of the query plan.") :arrow_upper_right:

