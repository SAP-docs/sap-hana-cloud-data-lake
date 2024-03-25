<!-- loioe245892799f64df68ade16f24f1ddfb0 -->

# LOAD\_PREFETCH\_LOOKAHEAD Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specify a higher prefetch lookahead value or lets the system set automatically based on the IO latency to improve performance with the LOAD statement.



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_o1y_kbg_htb"/>

## Syntax

```
LOAD_PREFETCH_LOOKAHEAD = <value>
```



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_mgb_mbg_htb"/>

## Allowed Values


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

\-1

</td>
<td valign="top">

Disables adaptive prefetching. The original prefetch approach where the lookahead value is 1 is used.

</td>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

Enables adaptive prefetching.

</td>
</tr>
<tr>
<td valign="top">

1 to 15

</td>
<td valign="top">

Specifies the lookahead value to use for adaptive prefetching to a maximum of 15.

</td>
</tr>
</table>



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_otr_mbg_htb"/>

## Default

0



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_cnd_2cw_cxb"/>

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



<a name="loioe245892799f64df68ade16f24f1ddfb0__section_nkb_wlb_dxb"/>

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

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

[LOAD_PREFETCH_LOOKAHEAD Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/912d8f5b53a54ea5ad4c23fbf5198644.html "Specify a higher prefetch lookahead value or lets the system set automatically based on the IO latency to improve performance with the LOAD statement.") :arrow_upper_right:

