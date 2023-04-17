<!-- loioaa37821e445f4177b189aad7442f104d -->

# TEMP\_EXTRACT\_COMPRESS Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioaa37821e445f4177b189aad7442f104d__section_ln4_w5h_mrb"/>

## Syntax

```
TEMP_EXTRACT_COMPRESS = { ON | OFF }
```



<a name="loioaa37821e445f4177b189aad7442f104d__section_i5y_w5h_mrb"/>

## Allowed Values

ON, OFF



<a name="loioaa37821e445f4177b189aad7442f104d__section_epq_x5h_mrb"/>

## Default

OFF



<a name="loioaa37821e445f4177b189aad7442f104d__section_p3v_syc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioaa37821e445f4177b189aad7442f104d__section_zyf_y5h_mrb"/>

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



<a name="loioaa37821e445f4177b189aad7442f104d__section_wsx_y5h_mrb"/>

## Remarks

This option cannot be used with the TEMP\_EXTRACT\_APPEND, TEMP\_EXTRACT\_SIZE, or TEMP\_EXTRACT\_SIZE*<n\>* options.

In parallel mode, the TEMP\_EXTRACT\_FILE\_EXTENSION option must be set to gz or '' \(empty string\). In serial mode, the TEMP\_EXTRACT\_NAME*<n\>* option must end with .gz.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md)

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_COMPRESS Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/aef24bc01a494d68b62e2b6dfeabff56.html "Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.") :arrow_upper_right:

