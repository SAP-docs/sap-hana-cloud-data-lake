<!-- loio35a8282ba03846b5a1f414244a91f046 -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_MAX\_RETRY\_ATTEMPTS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the number of consecutive failures of the same refresh request that can occur before it is no longer requeued by the materialized view auto refresh manager.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio35a8282ba03846b5a1f414244a91f046__section_mmt_5yd_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_MAX_RETRY_ATTEMPTS = <value>
```



<a name="loio35a8282ba03846b5a1f414244a91f046__section_j1z_xyd_qrb"/>

## Allowed Values

Integer



<a name="loio35a8282ba03846b5a1f414244a91f046__section_xvj_yyd_qrb"/>

## Default

5



<a name="loio35a8282ba03846b5a1f414244a91f046__section_edd_3pb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio35a8282ba03846b5a1f414244a91f046__section_ld5_1zd_qrb"/>

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



<a name="loio35a8282ba03846b5a1f414244a91f046__section_ipl_bzd_qrb"/>

## Remarks

Once the limit is exceeded, the refresh request is dropped. If the AUTO materialized view that had its refresh request dropped remains stale, it is detected by the next polling request and a new refresh request for the materialized view is queued.

**Related Information**  


[MATERIALIZED_VIEW_AUTO_REFRESH_MAX_RETRY_ATTEMPTS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/cfffe33a255f4593ae3412a93b50d2ab.html "Controls the number of consecutive failures of the same refresh request that can occur before it is no longer requeued by the materialized view auto refresh manager.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

