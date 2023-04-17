<!-- loio38858a2d4f3844f1a55421078ad2f90d -->

# TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio38858a2d4f3844f1a55421078ad2f90d__section_bmy_vzh_mrb"/>

## Syntax

```
TEMP_EXTRACT_REGION = <string_expression>
```



<a name="loio38858a2d4f3844f1a55421078ad2f90d__section_j45_wzh_mrb"/>

## Allowed Values

The valid AWS region identifier. For the latest list of valid AWS region identifiers, consult the Amazon S3 documentation.

```
SET TEMPORARY OPTION TEMP_EXTRACT_REGION = 'us-east-2';
```



<a name="loio38858a2d4f3844f1a55421078ad2f90d__section_owg_xzh_mrb"/>

## Default

If you don’t specify a region, then the system selects the region where the data lake Relational Engine resides. You must specify the server resides.



<a name="loio38858a2d4f3844f1a55421078ad2f90d__section_vp4_cxc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio38858a2d4f3844f1a55421078ad2f90d__section_d21_yzh_mrb"/>

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



<a name="loio38858a2d4f3844f1a55421078ad2f90d__section_ygs_yzh_mrb"/>

## Remarks

Used for data extraction from data lake Relational Engine to the Amazon S3 bucket.

Doesn’t apply to Azure Blob storage.

Use TEMP\_EXTRACT\_ACCESS\_KEY\_ID with the TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY, TEMP\_EXTRACT\_NAME*<N\>*, and TEMP\_EXTRACT\_REGION options in your data extraction query.

For example syntax, see *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-sap-hana-db-22fc37e.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md)

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-sap-hana-64f7adf.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_REGION Option (Deprecated) for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/5a091832c0bf4722b78c5358f477071a.html "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.") :arrow_upper_right:
