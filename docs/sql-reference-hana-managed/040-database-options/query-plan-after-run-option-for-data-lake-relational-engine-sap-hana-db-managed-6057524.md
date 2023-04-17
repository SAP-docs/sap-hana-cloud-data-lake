<!-- loio60575248dc354201b6191e03d24b21fc -->

# QUERY\_PLAN\_AFTER\_RUN Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Prints the entire query plan after query execution is complete.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio60575248dc354201b6191e03d24b21fc__section_i3k_cdt_lrb"/>

## Syntax

```
QUERY_PLAN_AFTER_RUN = { ON | OFF }
```



<a name="loio60575248dc354201b6191e03d24b21fc__section_swt_cdt_lrb"/>

## Allowed Values

ON, OFF



<a name="loio60575248dc354201b6191e03d24b21fc__section_c2r_ddt_lrb"/>

## Default

ON



<a name="loio60575248dc354201b6191e03d24b21fc__section_jy2_btb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio60575248dc354201b6191e03d24b21fc__section_dml_2dt_lrb"/>

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



<a name="loio60575248dc354201b6191e03d24b21fc__section_ohf_fdt_lrb"/>

## Remarks

When QUERY\_PLAN\_AFTER\_RUN is turned ON, the query plan is printed after the query has finished running. This allows the query plan to include additional information, such as the actual number of rows passed on from each node of the query.

For this option to work, the QUERY\_PLAN option must be set to ON. You can use this option in conjunction with QUERY\_DETAIL to generate additional information in the query plan report.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_DETAIL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](query-detail-option-for-data-lake-relational-engine-sap-hana-db-managed-4aa5427.md "Specifies whether or not to include additional query information in the Query Detail section of the query plan.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[QUERY_PLAN_AFTER_RUN Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a64dbdd384f21015983ac21e25acaab1.html "Prints the entire query plan after query execution is complete.") :arrow_upper_right:
