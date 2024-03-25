<!-- loioa65cd33584f210159126844d7b32b6a8 -->

# TEMP\_EXTRACT\_DIRECTORY Option for Data Lake Relational Engine

Controls whether a user is allowed to use the data extraction facility. Also controls the directory into which temp extract files are placed, and overrides a directory path specified in the TEMP\_EXTRACT\_NAME*<N\>* option.



<a name="loioa65cd33584f210159126844d7b32b6a8__section_ah3_h5q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65cd33584f210159126844d7b32b6a8__temp_extract_directory_syntax1"/>

## Syntax

```
TEMP_EXTRACT_DIRECTORY = <string_expression>
```



<a name="loioa65cd33584f210159126844d7b32b6a8__temp_extract_directory_values1"/>

## Allowed Values

A string defining the directory path. The string can be:


<table>
<tr>
<th valign="top">

*<string\_expression\>* type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

data lake Files storage

</td>
<td valign="top">

The data lake Files container you're extracting to.

</td>
<td valign="top">

hdlfs://analytics

</td>
</tr>
<tr>
<td valign="top">

Azure storage

</td>
<td valign="top">

The Azure container you're extracting to.

</td>
<td valign="top">

bb://mycontainer/myblob

</td>
</tr>
<tr>
<td valign="top">

AWS storage

</td>
<td valign="top">

The S3 bucket you're extracting to.

</td>
<td valign="top">

s3://mybucket/mydata

</td>
</tr>
</table>



<a name="loioa65cd33584f210159126844d7b32b6a8__temp_extract_directory_default1"/>

## Default

' ' \(the empty string\)



<a name="loioa65cd33584f210159126844d7b32b6a8__temp_extract_directory_priv1"/>

## Privileges

Privilege Category: SYSTEM



### 

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioa65cd33584f210159126844d7b32b6a8__temp_extract_directory_scope1"/>

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



<a name="loioa65cd33584f210159126844d7b32b6a8__temp_extract_directory_remarks1"/>

## Remarks

If the TEMP\_EXTRACT\_DIRECTORY option is:

-   Set to a valid directory path, then temp extract files are placed in that directory – overriding a path specified in the TEMP\_EXTRACT\_NAME*<N\>* options.
-   Set to an invalid directory path, then an error occurs: ***Files does not exist File: *<invalid path\>****
-   Blank, then temporary extract files are placed in directories according to their specification in TEMP\_EXTRACT\_NAME*<N\>*.

For example syntax, see [(Deprecated) Unloading Data to the External Object Store Using the Data Extraction Facility](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/a732a39184f21015979f85151aea1b30.html "The data extraction facility is a group of database options that unload data to the external object store.") :arrow_upper_right:.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_DIRECTORY Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b9f214cdab094fc885a1900d77570fff.html "Controls whether a user is allowed to use the data extraction facility. Also controls the directory into which temp extract files are placed, and overrides a directory path specified in the TEMP_EXTRACT_NAMEN option.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine](temp-extract-name-n-option-for-data-lake-relational-engine-a65dd19.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

