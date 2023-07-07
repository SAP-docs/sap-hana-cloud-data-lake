<!-- loio0db49375bae040b7a9a0d3df26d843ba -->

# TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine

Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio0db49375bae040b7a9a0d3df26d843ba__temp_extrac_secret_access_syntax1"/>

## Syntax

```
TEMP_EXTRACT_SECRET_ACCESS_KEY = <string_expression>
```



<a name="loio0db49375bae040b7a9a0d3df26d843ba__temp_extrac_secret_access_values1"/>

## Allowed Values

Enter the credential key strings as-is. All characters within the AWS secret access key are valid in data lake Relational Engine and don’t require escape codes. Example:

```
TEMP_EXTRACT_SECRET_ACCESS_KEY = 'CMKCKQUHQFPP8EXAMPLE/123abc/Example12'
```



<a name="loio0db49375bae040b7a9a0d3df26d843ba__temp_extrac_secret_access_default1"/>

## Default

NULL.



<a name="loio0db49375bae040b7a9a0d3df26d843ba__temp_extrac_secret_access_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio0db49375bae040b7a9a0d3df26d843ba__temp_extrac_secret_access_scope1"/>

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



<a name="loio0db49375bae040b7a9a0d3df26d843ba__temp_extrac_secret_access_remarks1"/>

## Remarks

Used for data extraction from data lake Relational Engine to an Amazon S3 bucket.

Doesn’t apply to Azure Blob storage.

Use TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY with the TEMP\_EXTRACT\_ACCESS\_KEY\_ID, TEMP\_EXTRACT\_NAME*<N\>*, and TEMP\_EXTRACT\_REGION options in your data extraction query.

For example syntax, see *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[TEMP_EXTRACT_SECRET_ACCESS_KEY Option (Deprecated) for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/64f7adf55c7343a7bd2203ee50a46f96.html "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-924c9f8.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine](temp-extract-name-n-option-for-data-lake-relational-engine-a65dd19.md "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.")

[TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine](temp-extract-region-option-deprecated-for-data-lake-relational-engine-5a09183.md "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_2_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

