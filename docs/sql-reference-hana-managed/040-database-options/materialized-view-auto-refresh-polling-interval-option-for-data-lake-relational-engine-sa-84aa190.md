<!-- loio84aa190c7a8f463196bd9755c6146a29 -->

# MATERIALIZED\_VIEW\_AUTO\_REFRESH\_POLLING\_INTERVAL Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the amount of time \(in minutes\) between polling refresh requests executed by the materialized view auto refresh manager.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio84aa190c7a8f463196bd9755c6146a29__section_wgn_4zd_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_AUTO_REFRESH_POLLING_INTERVAL  = <value>
```



<a name="loio84aa190c7a8f463196bd9755c6146a29__section_bjw_4zd_qrb"/>

## Allowed Values

Integer, in minutes. Lower limit is 1 with no upper limit.



<a name="loio84aa190c7a8f463196bd9755c6146a29__section_n3j_pzd_qrb"/>

## Default

2



<a name="loio84aa190c7a8f463196bd9755c6146a29__section_pdy_s4b_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio84aa190c7a8f463196bd9755c6146a29__section_f5d_rzd_qrb"/>

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


[MATERIALIZED_VIEW_AUTO_REFRESH_POLLING_INTERVAL Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/beb258e2c5044c44aebc49f3d6318ca2.html "Controls the amount of time (in minutes) between polling refresh requests executed by the materialized view auto refresh manager.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

