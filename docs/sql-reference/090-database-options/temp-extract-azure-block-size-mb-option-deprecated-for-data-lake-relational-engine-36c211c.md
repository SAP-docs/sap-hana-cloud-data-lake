<!-- loio36c211c5896e4b88ad8d275a785615f8 -->

# TEMP\_EXTRACT\_AZURE\_BLOCK\_SIZE\_MB Option \(Deprecated\) for Data Lake Relational Engine

Specifies the size of blocks in an Azure block blob, in MB.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio36c211c5896e4b88ad8d275a785615f8__temp_extract_azure_block_syntax1"/>

## Syntax

```
TEMP_EXTRACT_AZURE_BLOCK_SIZE_MB = <number_expression>
```



<a name="loio36c211c5896e4b88ad8d275a785615f8__temp_extract_azure_block_values1"/>

## Allowed Values

1–100 MB



<a name="loio36c211c5896e4b88ad8d275a785615f8__temp_extract_azure_block_default1"/>

## Default

10 MB



<a name="loio36c211c5896e4b88ad8d275a785615f8__temp_extract_azure_block_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio36c211c5896e4b88ad8d275a785615f8__temp_extract_azure_block_scope1"/>

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



<a name="loio36c211c5896e4b88ad8d275a785615f8__temp_extract_azure_block_remarks1"/>

## Remarks

Can be used when extracting data lake Relational Engine data to one or more block blobs in an Azure storage account container.

Doesn’t apply to Amazon S3 storage.

A block blob is composed of blocks. Each block can be a different size, up to a maximum size of 100 MB. Each block blob can contain up to 50,000 blocks. In data lake Relational Engine, the default block size is 10 MB. Using this default block size, the maximum size of a block blob is 500 GB \(10 MB x 50,000 blocks\).

If you need to extract more than 500 GB to the block blob, then use this option to increase the block size from its 10-MB default.

> ### Note:  
> In Azure, the maximum size limit for a single block blob is 4.75 TB. If you're extracting more than 4.75 TB of data lake Relational Engine data, extract to multiple block blobs.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/84a37a4b73ff4ba1ae53aad6b4c94803.html "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_AZURE_BLOCK_SIZE_MB Option (Deprecated) for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/802669466312448eb96e92e1270a5fa8.html "Specifies the size of blocks in an Azure block blob, in MB.") :arrow_upper_right:

