<!-- loio5a091832c0bf4722b78c5358f477071a -->

# TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine

Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.



<a name="loio5a091832c0bf4722b78c5358f477071a__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio5a091832c0bf4722b78c5358f477071a__temp_extract_region_syntax1"/>

## Syntax

```
TEMP_EXTRACT_REGION = <string_expression>;
```



<a name="loio5a091832c0bf4722b78c5358f477071a__temp_extract_region_values1"/>

## Allowed Values

The valid AWS region identifier. For the latest list of valid AWS region identifiers, consult the Amazon S3 documentation.

```
SET TEMPORARY OPTION TEMP_EXTRACT_REGION = 'us-east-2';
```



<a name="loio5a091832c0bf4722b78c5358f477071a__temp_extract_region_default1"/>

## Default

If you don’t specify a region, then the system selects the region where the data lake Relational Engine resides. You must specify the server resides.



<a name="loio5a091832c0bf4722b78c5358f477071a__temp_extract_region_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio5a091832c0bf4722b78c5358f477071a__temp_extract_region_scope1"/>

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



<a name="loio5a091832c0bf4722b78c5358f477071a__temp_extract_region_remarks1"/>

## Remarks

Used for data extraction from data lake Relational Engine to the Amazon S3 bucket.

Doesn’t apply to Azure Blob storage.

Use TEMP\_EXTRACT\_ACCESS\_KEY\_ID with the TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY, TEMP\_EXTRACT\_NAME*<N\>*, and TEMP\_EXTRACT\_REGION options in your data extraction query.

For example syntax, see *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-924c9f8.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine](temp-extract-name-n-option-for-data-lake-relational-engine-a65dd19.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-0db4937.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_REGION Option (Deprecated) for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/38858a2d4f3844f1a55421078ad2f90d.html "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.") :arrow_upper_right:

