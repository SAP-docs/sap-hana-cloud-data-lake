<!-- loio7f412b6887e147db9f22903b91bba87d -->

# MATERIALIZED\_VIEW\_STALENESS\_CHECK Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls which materialized views are checked for staleness.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio7f412b6887e147db9f22903b91bba87d__section_wsj_s12_qrb"/>

## Syntax

```
MATERIALIZED_VIEW_STALENESS_CHECK= { 0 | 1 | 2)
```



<a name="loio7f412b6887e147db9f22903b91bba87d__section_z42_t12_qrb"/>

## Allowed Values

0 - \(OFF\) No materialized views are checked for staleness when they are read.

1 - \(Default\) Only AUTO REFRESH materialized views are checked for staleness when they are read.

2 - All materialized views are checked for staleness when they are read.



<a name="loio7f412b6887e147db9f22903b91bba87d__section_ifs_t12_qrb"/>

## Default

1



<a name="loio7f412b6887e147db9f22903b91bba87d__section_w4y_ypb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio7f412b6887e147db9f22903b91bba87d__section_ods_512_qrb"/>

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

**Related Information**  


[MATERIALIZED_VIEW_STALENESS_CHECK Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/aa769ea2e3b54c92a0b6b2fd1f7e44bc.html "Controls which materialized views are checked for staleness.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

