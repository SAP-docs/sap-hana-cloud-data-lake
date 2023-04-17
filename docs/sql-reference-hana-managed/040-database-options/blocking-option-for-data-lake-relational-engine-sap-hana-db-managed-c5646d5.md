<!-- loioc5646d5b730a431dacb60c07624d25db -->

# BLOCKING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the behavior in response to locking conflicts.BLOCKING isn't supported on worker nodes.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioc5646d5b730a431dacb60c07624d25db__section_erb_nz4_3qb"/>

## Syntax

```
BLOCKING = { ON | OFF }
```



<a name="loioc5646d5b730a431dacb60c07624d25db__section_m3k_spy_brb"/>

## Allowed Values

ON, OFF



<a name="loioc5646d5b730a431dacb60c07624d25db__section_ogt_1xn_hrb"/>

## Default

OFF



<a name="loioc5646d5b730a431dacb60c07624d25db__section_q42_xxv_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioc5646d5b730a431dacb60c07624d25db__section_dmr_2nb_dxb"/>

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



<a name="loioc5646d5b730a431dacb60c07624d25db__section_g5j_bqy_brb"/>

## Remarks

When BLOCKING is off, a transaction receives an error when it attempts a write operation and is blocked by the read lock of another transaction.

When BLOCKING is on, any transaction attempting to obtain a lock that conflicts with an existing lock held by another transaction waits until every conflicting lock is released or until the BLOCKING\_TIMEOUT is reached. If the lock isn’t released within BLOCKING\_TIMEOUT milliseconds, then an error is returned for the waiting transaction.

> ### Note:  
> BLOCKING isn't supported on worker nodes of the multiplex cluster. SAP HANA servers can only access worker nodes.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[BLOCKING Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a62e391684f21015b33ae00f1e29d81a.html "Controls the behavior in response to locking conflicts. BLOCKING isn&apos;t supported on worker nodes.") :arrow_upper_right:

