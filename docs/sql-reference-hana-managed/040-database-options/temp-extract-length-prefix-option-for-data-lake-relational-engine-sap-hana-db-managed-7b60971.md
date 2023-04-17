<!-- loio7b609716b74d46c588d7f5a8c64738e7 -->

# TEMP\_EXTRACT\_LENGTH\_PREFIX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Adds a prefix field of specified length \(byte\) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio7b609716b74d46c588d7f5a8c64738e7__section_khh_vxh_mrb"/>

## Syntax

```
TEMP_EXTRACT_LENGTH_PREFIX = <value>
```



<a name="loio7b609716b74d46c588d7f5a8c64738e7__section_mdt_vxh_mrb"/>

## Allowed Values

0, 1, 2, 4



<a name="loio7b609716b74d46c588d7f5a8c64738e7__section_tm5_wxh_mrb"/>

## Default

0 \(zero\)



<a name="loio7b609716b74d46c588d7f5a8c64738e7__section_acr_vyc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio7b609716b74d46c588d7f5a8c64738e7__section_sxy_xxh_mrb"/>

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



<a name="loio7b609716b74d46c588d7f5a8c64738e7__section_iwp_yxh_mrb"/>

## Remarks

If you do not specify TEMP\_EXTRACT\_LENGTH\_PREFIX, or you specify 0 \(the default\), the data extraction facility does not generate a prefix length field.

When you specify any other valid value for TEMP\_EXTRACT\_LENGTH\_PREFIX, the data extraction facility uses that specified value for the length \(byte\) of the prefix field that holds the actual data length, adding it before the actual data for a varchar or varbinary column, including the length for trailing spaces and zeros in the column. If the TEMP\_EXTRACT\_VARYING option is not set, however, the total length of the actual column data in the extracted file is its declared length in a fixed-length format. For example, the data extraction facility always generates 10 bytes for a varchar\(10\) column, necessary to make the file format fixed length.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-varying-option-for-data-lake-relational-engine-sap-hana-db-managed-a975dc5.md "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_LENGTH_PREFIX Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/1126138de454476ebec9e52012d4511a.html "Adds a prefix field of specified length (byte) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.") :arrow_upper_right:

