<!-- loio18ef1dc498014c8387888ec6f61220bf -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_MAX\_CONCURRENT\_REQUESTS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the maximum number of materialized view refresh requests that can be concurrently running in data lake Relational Engine.



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_e5j_35d_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_MAX_CONCURRENT_REQUESTS = <value>;
```



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_l2l_j5d_qrb"/>

## Allowed Values

Integer, lower limit is 0 with no upper limit.



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_oxd_k5d_qrb"/>

## Default

10



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_mjj_dpb_dxb"/>

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



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_bdk_m5d_qrb"/>

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

No

</td>
<td valign="top">

No

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

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_xqz_m5d_qrb"/>

## Remarks

Once the limit is reached, refresh requests will be queued and will remain queued until the number of concurrent requests decreases below the limit.

**Related Information**  


[MATERIALIZED_VIEW_AUTO_REFRESH_MAX_CONCURRENT_REQUESTS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/d4bd911e17014fa7be4c4719c5cb638b.html "Controls the maximum number of materialized view refresh requests that can be concurrently running in data lake Relational Engine.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

