<!-- loio01b1d2db6b4441a2a33b49e83e17187e -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_RETRY\_INTERVAL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the amount of time \(in seconds\) to wait before a failed refresh request is requeued by the materialized view auto refresh manager.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio01b1d2db6b4441a2a33b49e83e17187e__section_m5k_d12_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_RETRY_INTERVAL = <value>
```



<a name="loio01b1d2db6b4441a2a33b49e83e17187e__section_f3b_212_qrb"/>

## Allowed Values

Integer, in seconds. Lower limit is 0 with no upper limit.



<a name="loio01b1d2db6b4441a2a33b49e83e17187e__section_ut4_212_qrb"/>

## Default

3



<a name="loio01b1d2db6b4441a2a33b49e83e17187e__section_ofq_qpb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio01b1d2db6b4441a2a33b49e83e17187e__section_qyx_f12_qrb"/>

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

**Related Information**  


[MATERIALIZED_VIEW_AUTO_REFRESH_RETRY_INTERVAL Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/054a74ba291840e7bb01d3bc9588f1a2.html "Controls the amount of time (in seconds) to wait before a failed refresh request is requeued by the materialized view auto refresh manager.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

