<!-- loio7ac82c4f1cfb46bbb18966f957d91b3d -->

# MATERIALIZED\_VIEW\_STALENESS\_LIMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the maximum stale time limit, in the specified units of time.



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_opx_gb2_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_STALENESS_LIMIT = { Fresh | N { Minute[s] | Hour[s] | Day[s] | Week[s] | Month[s] } }
```



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_bs4_hb2_qrb"/>

## Allowed Values

N is an integer greater than 0 where:

1 week = 7 days

1 month = 30 days.

Fresh = All stale reads return an error.



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_eyh_3b2_qrb"/>

## Default

30 minutes



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_zdd_l4b_dxb"/>

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



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_qhk_jb2_qrb"/>

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



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_cyq_kb2_qrb"/>

## Remarks

This option is not supported if MATERIALIZED\_VIEW\_STALENESS\_CHECK is set to 0 \(OFF\).



<a name="loio7ac82c4f1cfb46bbb18966f957d91b3d__section_x2j_lh2_qrb"/>

## Examples

This example sets the staleness check to 30 minutes.

```
SET TEMPORARY OPTION materialized_view_staleness_limit='30 Minutes';
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[MATERIALIZED_VIEW_STALENESS_LIMIT Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/f444eb30bf634e93a0e63edb1a85ffa8.html "Controls the maximum stale time limit, in the specified units of time.") :arrow_upper_right:

