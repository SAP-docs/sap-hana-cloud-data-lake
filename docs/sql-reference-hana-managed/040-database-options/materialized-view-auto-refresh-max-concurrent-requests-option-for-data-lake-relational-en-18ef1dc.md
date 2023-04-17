<!-- loio18ef1dc498014c8387888ec6f61220bf -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_MAX\_CONCURRENT\_REQUESTS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the maximum number of materialized view refresh requests that can be concurrently running in data lake Relational Engine.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio18ef1dc498014c8387888ec6f61220bf__section_e5j_35d_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_MAX_CONCURRENT_REQUESTS = <value>
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

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



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


[MATERIALIZED_VIEW_AUTO_REFRESH_MAX_CONCURRENT_REQUESTS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/d4bd911e17014fa7be4c4719c5cb638b.html "Controls the maximum number of materialized view refresh requests that can be concurrently running in data lake Relational Engine.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

