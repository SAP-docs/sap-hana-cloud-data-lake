<!-- loioa65dd19984f21015ae79a8e590956ad0 -->

# TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine

Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.



<a name="loioa65dd19984f21015ae79a8e590956ad0__section_ajq_xqq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa65dd19984f21015ae79a8e590956ad0__TEMP_EXTRACT_NAME_syntax1"/>

## Syntax

```
TEMP_EXTRACT_NAME<N> = <string_expression>
```



<a name="loioa65dd19984f21015ae79a8e590956ad0__values1"/>

## Allowed Values

A specially formed name specifying either:

-   The pathname to an object file in a data lake Files container. The prefix "`hdlfs:`" identifies the path as a data lake Files path.

    For example, this *<string\_expression\>* extracts data to a container named `analytics` in data lake Files:

    ```
    TEMP_EXTRACT_NAME1 = 'hdlfs://analytics/Q3trend.csv'
    ```

    If you don't specify a container name, it extracts to the default data lake Files container:

    ```
    TEMP_EXTRACT_NAME1 = 'hdlfs:///leaves.csv'
    ```

-   **Amazon S3 storage**: The object name of the file in the Amazon S3 bucket you're extracting to. For example:

    ```
    TEMP_EXTRACT_NAME2 = s3://<bucket_name>/<object_name>
    ```

-   **Azure Blob storage**: The name of the block blob you're extracting to. `bb:` indicates a block blob. For example:

    ```
    TEMP_EXTRACT_NAME2 = bb://<container_name>/<folder_name>/<block_blob_name>
    ```




<a name="loioa65dd19984f21015ae79a8e590956ad0__TEMP_EXTRACT_NAME_default1"/>

## Default

Null. If you don’t specify a file name, no file is extracted.



<a name="loioa65dd19984f21015ae79a8e590956ad0__TEMP_EXTRACT_NAME_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa65dd19984f21015ae79a8e590956ad0__TEMP_EXTRACT_NAME_scope1"/>

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



<a name="loioa65dd19984f21015ae79a8e590956ad0__TEMP_EXTRACT_NAME_remarks1"/>

## Remarks

Used for data extraction from data lake Relational Engine to either a data lake Files container, or to Azure Blob storage, or to an Amazon S3 bucket.

Azure block blobs have a size limit of 4.75 TB. Amazon S3 objects have a size limit of 5 TB. If your extraction exceeds these limits, then you require multiple output files. Use TEMP\_EXTRACT\_NAME*<N\>* if the size limit in TEMP\_EXTRACT\_NAME1 is too small for the amount of data you're extracting.

Files must be smaller than the Azure and Amazon S3 limits. For example, if you're extracting 16 TB to Azure Blob storage, you define four files: TEMP\_EXTRACT\_NAME1, TEMP\_EXTRACT\_NAME2, and TEMP\_EXTRACT\_NAME3 of 4.75 TB each, and TEMP\_EXTRACT\_NAME4 with 1.75 TB.

At the end of your data extraction SELECT statement, set TEMP\_EXTRACT\_NAME*<N\>* to an empty string. If you don't disable, then the next SELECT statement overwrites the object in cloud storage.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage* and *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP_EXTRACT_NAME<N> Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/1f0b3e1f87c948fd881490465f5eea24.html "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.") :arrow_upper_right:

[TEMP\_EXTRACT\_APPEND Option for Data Lake Relational Engine](temp-extract-append-option-for-data-lake-relational-engine-a65b43e.md "Specifies that any rows extracted by the data extraction facility are added to the end of an output file.")

[TEMP\_EXTRACT\_DIRECTORY Option for Data Lake Relational Engine](temp-extract-directory-option-for-data-lake-relational-engine-a65cd33.md "Controls whether a user is allowed to use the data extraction facility. Also controls the directory into which temp extract files are placed, and overrides a directory path specified in the TEMP_EXTRACT_NAMEN option.")

[TEMP\_EXTRACT\_SIZE<N\> Options for Data Lake Relational Engine](temp-extract-size-n-options-for-data-lake-relational-engine-a6615dd.md "Specifies the maximum sizes of the corresponding output files used by the data extraction facility.")

