<!-- loio2e6a10d296ec4bd6a7209e65e0171171 -->

# FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Enforces sizing limits for explicit and implicit NBit columns.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio2e6a10d296ec4bd6a7209e65e0171171__section_hpz_s23_3rb"/>

## Syntax

```
FP_NBIT_ENFORCE_LIMITS = { ON | OFF }
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

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



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

[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-sap-hana-db-managed-829744c.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-sap-hana-db-managed-9035f14.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[FP_NBIT_ENFORCE_LIMITS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a874045684f21015abbbd6b7d63613e5.html "Enforces sizing limits for explicit and implicit NBit columns.") :arrow_upper_right:

