<!-- loio176630977a7d4a46b04fe1f7b30fd9c2 -->

# QUERY\_PLAN\_TEXT\_ACCESS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Enables or prevents users from accessing query plans from the Interactive SQL client or from using SQL functions to get plans.



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_kd4_v2t_lrb"/>

## Syntax

```
QUERY_PLAN_TEXT_ACCESS = { ON | OFF };
```



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_bdy_v2t_lrb"/>

## Allowed Values

ON, OFF



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_fqm_w2t_lrb"/>

## Default

OFF



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_q1s_vrb_dxb"/>

## Privileges

Privilege Category: SYSTEM



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

-   Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



</dd>
</dl>



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_oyh_1ft_lrb"/>

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



<a name="loio176630977a7d4a46b04fe1f7b30fd9c2__section_rx5_cft_lrb"/>

## Remarks

When QUERY\_PLAN\_TEXT\_ACCESS option is ON, users can view, save, and print query plans from the Interactive SQL client. When the option is OFF, query plans are not cached, and other query plan-related database options have no effect on the query plan that is shown from the Interactive SQL client. This error message appears:

```
No plan available. The database option QUERY_PLAN_TEXT_ACCESS is OFF.
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[QUERY\_PLAN\_TEXT\_CACHING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](query-plan-text-caching-option-for-data-lake-relational-engine-sap-hana-db-managed-bee56c4.md "Allows you to specify whether or not data lake Relational Engine generates and caches IQ plans for queries executed by the user.")

[QUERY_PLAN_TEXT_ACCESS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a64f443284f21015acbbd8e919d9c49b.html "Enables or prevents users from accessing query plans from the Interactive SQL client or from using SQL functions to get plans.") :arrow_upper_right:

