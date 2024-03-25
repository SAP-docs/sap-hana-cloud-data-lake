<!-- loio60575248dc354201b6191e03d24b21fc -->

# QUERY\_PLAN\_AFTER\_RUN Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Prints the entire query plan after query execution is complete.



<a name="loio60575248dc354201b6191e03d24b21fc__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method and whether you are setting the option temporarily or permanently:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user:

</b></dt>
<dd>

-   To set a database option permanently, use REMOTE\_EXECUTE.

    Requires one of:

    -   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
    -   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

    -   See [REMOTE\_EXECUTE Guidance and Examples for Setting Permanent Database Options](remote-execute-guidance-and-examples-for-setting-permanent-database-options-0023bea.md).


-   To set a database option temporarily, use the SET\_TEMPORARY\_OPTION procedure, which requires you be a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.

    -   See [SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md).





</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



</dd>
</dl>



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

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[QUERY\_DETAIL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](query-detail-option-for-data-lake-relational-engine-sap-hana-db-managed-4aa5427.md "Specifies whether or not to include additional query information in the Query Detail section of the query plan.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[QUERY_PLAN_AFTER_RUN Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a64dbdd384f21015983ac21e25acaab1.html "Prints the entire query plan after query execution is complete.") :arrow_upper_right:

