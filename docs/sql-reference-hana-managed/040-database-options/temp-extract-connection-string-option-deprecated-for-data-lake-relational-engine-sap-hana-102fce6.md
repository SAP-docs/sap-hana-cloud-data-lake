<!-- loio102fce67fe5341fa983aca0a4e3143a7 -->

# TEMP\_EXTRACT\_CONNECTION\_STRING Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the connection string of your Azure storage account.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio102fce67fe5341fa983aca0a4e3143a7__section_fhr_pvh_mrb"/>

## Syntax

```
TEMP_EXTRACT_CONNECTION_STRING <string_expression>
```



<a name="loio102fce67fe5341fa983aca0a4e3143a7__section_pdb_qvh_mrb"/>

## Allowed Values

The Azure storage account connection string. Example connection string:

```
DefaultEndpointsProtocol=https;AccountName=example;AccountKey=example_key;EndpointSuffix=core.windows.net
```

> ### Tip:  
> You can find your connection string in Azure portal. From your storage account, navigate to *Settings* \> *Access Keys*. Locate the *Connection string* section and copy the connection string to the clipboard.



<a name="loio102fce67fe5341fa983aca0a4e3143a7__section_qjv_rvh_mrb"/>

## Default

Null



<a name="loio102fce67fe5341fa983aca0a4e3143a7__section_dxv_yqc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio102fce67fe5341fa983aca0a4e3143a7__section_n11_tvh_mrb"/>

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



<a name="loio102fce67fe5341fa983aca0a4e3143a7__section_mpk_tvh_mrb"/>

## Remarks

Used when extracting data lake Relational Engine data to one or more block blobs in an Azure storage account container.

Doesn’t apply to Amazon S3 storage.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_CONNECTION_STRING Option (Deprecated) for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/b96926be0fc140889e7cefa3565b0f1f.html "Specifies the connection string of your Azure storage account.") :arrow_upper_right:

