<!-- loio3122a9a6dcee455791a4097b41c21407 -->

# IDENTITY\_INSERT Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Enables users to insert values into or to update an IDENTITY or AUTOINCREMENT column.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio3122a9a6dcee455791a4097b41c21407__section_xvc_dns_lrb"/>

## Syntax

```
IDENTITY_INSERT = <datalake_table_name>
```



<a name="loio3122a9a6dcee455791a4097b41c21407__section_gln_dns_lrb"/>

## Allowed Values

= '*<tablename\>*'



<a name="loio3122a9a6dcee455791a4097b41c21407__section_tqt_2ns_lrb"/>

## Default

Option not set.



<a name="loio3122a9a6dcee455791a4097b41c21407__section_usr_4bw_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio3122a9a6dcee455791a4097b41c21407__section_qzg_bmb_dxb"/>

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

> ### Note:  
> If you set a user level option for the current option, the corresponding temporary option is also set. See *Scope and Duration of Database Options*.



<a name="loio3122a9a6dcee455791a4097b41c21407__section_rzr_4ns_lrb"/>

## Remarks

When IDENTITY\_INSERT is set, insert/update is enabled. A table name must be specified to identify the column to insert or update. If you are not the table owner, qualify the table name with the owner name.

To drop a table with an IDENTITY column, IDENTITY\_INSERT must not be set to that table.



<a name="loio3122a9a6dcee455791a4097b41c21407__section_iym_pns_lrb"/>

## Examples

If you use the table Employees to run explicit inserts:

```
SET TEMPORARY OPTION IDENTITY_INSERT = 'HDLADMIN.Employees'
```

To turn the option off, specify the equals sign and an empty string:

```
SET TEMPORARY OPTION IDENTITY_INSERT = ''
```

Illustrates the effect of user level options on temporary options \(see *Note*\), if you are connected to the database as HDLADMIN and enter:

```
SET OPTION IDENTITY_INSERT = 'Customers'
```

The value for the option is set to Customers for the user HDLADMIN and temporary for the current connection. Other users who subsequently connect to the database as HDLADMIN find their option value for IDENTITY\_INSERT is Customers also.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[IDENTITY_INSERT Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a63914eb84f21015b454db5374017eb5.html "Enables users to insert values into or to update an IDENTITY or AUTOINCREMENT column.") :arrow_upper_right:

