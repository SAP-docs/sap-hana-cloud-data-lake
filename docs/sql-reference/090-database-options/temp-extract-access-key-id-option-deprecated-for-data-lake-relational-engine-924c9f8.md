<!-- loio924c9f84b1d54194819442a1b03228b1 -->

# TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine

Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.



<a name="loio924c9f84b1d54194819442a1b03228b1__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio924c9f84b1d54194819442a1b03228b1__temp_extract_access_key_syntax1"/>

## Syntax

```
TEMP_EXTRACT_ACCESS_KEY_ID = <string_expression>
```



<a name="loio924c9f84b1d54194819442a1b03228b1__temp_extract_access_key_values1"/>

## Allowed Values

Enter the credential key strings as-is. All characters in the AWS access key are valid in data lake Relational Engine and don’t require escape codes.



<a name="loio924c9f84b1d54194819442a1b03228b1__temp_extract_access_key_default1"/>

## Default

Null.



<a name="loio924c9f84b1d54194819442a1b03228b1__temp_extract_access_key_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio924c9f84b1d54194819442a1b03228b1__temp_extract_access_key_scope1"/>

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



<a name="loio924c9f84b1d54194819442a1b03228b1__temp_extract_access_key_remarks1"/>

## Remarks

Use TEMP\_EXTRACT\_ACCESS\_KEY\_ID along with the options TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY, TEMP\_EXTRACT\_NAME*<N\>*, and TEMP\_EXTRACT\_REGION in your data extraction query.

Applies to Amazon S3 only. Doesn’t apply to Azure Blob storage.

For example syntax, see *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/84a37a4b73ff4ba1ae53aad6b4c94803.html "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.") :arrow_upper_right:

[TEMP_EXTRACT_NAME<N> Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/1f0b3e1f87c948fd881490465f5eea24.html "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.") :arrow_upper_right:

[TEMP_EXTRACT_REGION Option (Deprecated) for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/38858a2d4f3844f1a55421078ad2f90d.html "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.") :arrow_upper_right:

[TEMP_EXTRACT_SECRET_ACCESS_KEY Option (Deprecated) for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/64f7adf55c7343a7bd2203ee50a46f96.html "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.") :arrow_upper_right:

