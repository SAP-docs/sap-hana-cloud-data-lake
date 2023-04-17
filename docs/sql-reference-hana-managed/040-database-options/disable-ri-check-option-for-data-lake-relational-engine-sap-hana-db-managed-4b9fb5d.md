<!-- loio4b9fb5d8d0e24b1984950aa752543793 -->

# DISABLE\_RI\_CHECK Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Allows load, insert, update, or delete operations to bypass the referential integrity check, improving performance.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio4b9fb5d8d0e24b1984950aa752543793__section_pns_kyh_3rb"/>

## Syntax

```
DISABLE_RI_CHECK = { ON | OFF }
```



<a name="loio4b9fb5d8d0e24b1984950aa752543793__section_fvg_lyh_3rb"/>

## Allowed Values

ON, OFF



<a name="loio4b9fb5d8d0e24b1984950aa752543793__section_izp_lyh_3rb"/>

## Default

OFF



<a name="loio4b9fb5d8d0e24b1984950aa752543793__section_slc_jbw_cxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio4b9fb5d8d0e24b1984950aa752543793__section_lgb_gmb_dxb"/>

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



<a name="loio4b9fb5d8d0e24b1984950aa752543793__section_xwb_pyh_3rb"/>

## Remarks

Users are responsible for ensuring that no referential integrity violation occurs during requests while DISABLE\_RI\_CHECK is set to ON.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[DISABLE_RI_CHECK Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a635241084f21015aab4acfa1a173538.html "Allows load, insert, update, or delete operations to bypass the referential integrity check, improving performance.") :arrow_upper_right:

