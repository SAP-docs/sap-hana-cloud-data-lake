<!-- loioaf977f36d280410dba64b6bfe2608179 -->

# TEMP\_EXTRACT\_FILE\_PREFIX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Sets the prefix of file name for the generated output file of the data parallel extraction facility. *<thread\_ID\>* starts from 1. *<filecount\>* starts from 1 for each thread ID. The*<filecount\>* part increments when the size of the output file reaches the file size limit specified by the TEMP\_EXTRACT\_SIZE option.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioaf977f36d280410dba64b6bfe2608179__section_jjn_gxh_mrb"/>

## Syntax

```
TEMP_EXTRACT_FILE_PREFIX = <string>
```



<a name="loioaf977f36d280410dba64b6bfe2608179__section_lbx_gxh_mrb"/>

## Allowed Values

String containing a prefix of the output filename.



<a name="loioaf977f36d280410dba64b6bfe2608179__section_ypt_hxh_mrb"/>

## Default

*<prefix\>**<thread\_ID\>*\_*<filecount\>*



<a name="loioaf977f36d280410dba64b6bfe2608179__section_ehs_fxc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioaf977f36d280410dba64b6bfe2608179__section_bqy_3xh_mrb"/>

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



<a name="loioaf977f36d280410dba64b6bfe2608179__section_xpv_jxh_mrb"/>

## Remarks

Use parallel extraction to extract to data lake Files storage, Azure storage, or AWS storage.

The TEMP\_EXTRACT\_APPEND option is not compatible with the parallel extraction facility. If the output files do not already exist, parallel extraction facility creates the new files. If the output files already exist, the file contents are overwritten.

Use the parallel data extraction facility when the data set to extract is large and you need better performance. When the parallel extract is enabled, multiple output files could be generated depending on the number of threads used to extract in parallel.

If the TEMP\_EXTRACT\_DIRECTORY option is set to a valid directory path, parallel temp extract files are placed in that directory. If TEMP\_EXTRACT\_DIRECTORY option is blank, then parallel temp extract files are by default placed in the server startup directory.

To enable parallel extract, set TEMP\_EXTRACT\_FILE\_PREFIX but not TEMP\_EXTRACT\_NAME1.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_FILE_PREFIX Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/09cd773ef6924c119dd3adea2e91bd96.html "Sets the prefix of file name for the generated output file of the data parallel extraction facility. thread_ID starts from 1. filecount starts from 1 for each thread ID. Thefilecount part increments when the size of the output file reaches the file size limit specified by the TEMP_EXTRACT_SIZE option.") :arrow_upper_right:

