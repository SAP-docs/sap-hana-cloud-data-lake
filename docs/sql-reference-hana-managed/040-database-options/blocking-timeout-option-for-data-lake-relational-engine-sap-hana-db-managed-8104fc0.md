<!-- loio8104fc0cdf4143caa395e241e58db92a -->

# BLOCKING\_TIMEOUT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the length of time a transaction waits to obtain a lock. BLOCKING\_TIMEOUT is only supported when connectd directly to the co-ordinator.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio8104fc0cdf4143caa395e241e58db92a__section_ytj_2yn_hrb"/>

## Syntax

```
BLOCKING_TIMEOUT = <number_expression>
```



<a name="loio8104fc0cdf4143caa395e241e58db92a__section_e45_2yn_hrb"/>

## Allowed Values

Integer, in milliseconds.



<a name="loio8104fc0cdf4143caa395e241e58db92a__section_wmd_fyn_hrb"/>

## Default

0



<a name="loio8104fc0cdf4143caa395e241e58db92a__section_ybc_q1w_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio8104fc0cdf4143caa395e241e58db92a__section_rkl_qmb_dxb"/>

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



<a name="loio8104fc0cdf4143caa395e241e58db92a__section_okc_kyn_hrb"/>

## Remarks

When the blocking option is on, any transaction attempting to obtain a lock that conflicts with an existing lock waits for the indicated number of milliseconds for the conflicting lock to be released. If the lock is not released within blocking\_timeout milliseconds, an error is returned for the waiting transaction.

Set the option to 0 to force all transactions attempting to obtain a lock to wait until all conflicting transactions release their locks.

**Related Information**  


[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[BLOCKING_TIMEOUT Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a31619c984f2101582cbbe66dee24be8.html "Controls the length of time a transaction waits to obtain a lock. BLOCKING_TIMEOUT is only supported when connectd directly to the co-ordinator.") :arrow_upper_right:

