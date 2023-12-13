<!-- loio2e6a10d296ec4bd6a7209e65e0171171 -->

# FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Enforces sizing limits for explicit and implicit NBit columns.



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_dzz_4jj_kyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be set when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_hpz_s23_3rb"/>

## Syntax

```
FP_NBIT_ENFORCE_LIMITS = { ON | OFF };
```



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_kvj_t23_3rb"/>

## Allowed Values

ON, OFF



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_ihx_t23_3rb"/>

## Default

OFF



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_fqx_vbw_cxb"/>

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



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_ttl_dmb_dxb"/>

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



## Remarks



### 

DML operations check the FP\_NBIT\_ENFORCE\_LIMITS option when the number of distinct values in a column exceeds the explicit limit set in an IQ UNIQUE constraint, which is above the FP\_NBIT\_AUTOSIZE value, or when the dictionary size for an implicit NBit rollover exceeds the FP\_NBIT\_ROLLOVER\_MAX\_MB limit.

If FP\_NBIT\_ENFORCE\_LIMITS is set to:

-   ON – the DML operation throws an error and rolls back
-   OFF – the DML operation continues and the NBit dictionary limits are ignored

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SET\_TEMPORARY\_OPTION Procedure for SAP HANA Database](../080-sap-hana-database-for-data-lake-relational-engine/set-temporary-option-procedure-for-sap-hana-database-abcd703.md "Grant database options temporarily for the current connection only on a data lake Relational Engine relational container.")

[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-sap-hana-db-managed-829744c.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-sap-hana-db-managed-9035f14.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[FP_NBIT_ENFORCE_LIMITS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a874045684f21015abbbd6b7d63613e5.html "Enforces sizing limits for explicit and implicit NBit columns.") :arrow_upper_right:

