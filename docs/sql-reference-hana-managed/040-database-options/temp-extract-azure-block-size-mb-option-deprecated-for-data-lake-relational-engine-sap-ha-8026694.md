<!-- loio802669466312448eb96e92e1270a5fa8 -->

# TEMP\_EXTRACT\_AZURE\_BLOCK\_SIZE\_MB Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the size of blocks in an Azure block blob, in MB.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio802669466312448eb96e92e1270a5fa8__section_frq_j5h_mrb"/>

## Syntax

```
TEMP_EXTRACT_AZURE_BLOCK_SIZE_MB = <number_expression>
```



<a name="loio802669466312448eb96e92e1270a5fa8__section_b41_k5h_mrb"/>

## Allowed Values

1–100 MB



<a name="loio802669466312448eb96e92e1270a5fa8__section_nqp_k5h_mrb"/>

## Default

10 MB



<a name="loio802669466312448eb96e92e1270a5fa8__section_lys_svc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio802669466312448eb96e92e1270a5fa8__section_rrf_l5h_mrb"/>

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



<a name="loio802669466312448eb96e92e1270a5fa8__section_wzx_l5h_mrb"/>

## Remarks

Can be used when extracting data lake Relational Engine data to one or more block blobs in an Azure storage account container.

Doesn’t apply to Amazon S3 storage.

A block blob is composed of blocks. Each block can be a different size, up to a maximum size of 100 MB. Each block blob can contain up to 50,000 blocks. In data lake Relational Engine, the default block size is 10 MB. Using this default block size, the maximum size of a block blob is 500 GB \(10 MB x 50,000 blocks\).

If you need to extract more than 500 GB to the block blob, then use this option to increase the block size from its 10-MB default.

> ### Note:  
> In Azure, the maximum size limit for a single block blob is 4.75 TB. If you're extracting more than 4.75 TB of data lake Relational Engine data, extract to multiple block blobs.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_AZURE_BLOCK_SIZE_MB Option (Deprecated) for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/36c211c5896e4b88ad8d275a785615f8.html "Specifies the size of blocks in an Azure block blob, in MB.") :arrow_upper_right:

