<!-- loioc475f53096e540a9840e2f2e4c584ad4 -->

# TEMP\_EXTRACT\_SIZE<N\> Options for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_zvd_wsc_dxb"/>

## Syntax

```
TEMP_EXTRACT_NAME<N> = <string_expression>
```



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_yg5_wsc_dxb"/>

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




<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_jtq_xsc_dxb"/>

## Default

Null. If you don’t specify a file name, no file is extracted.



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_p5f_ysc_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_j4z_ysc_dxb"/>

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



<a name="loioc475f53096e540a9840e2f2e4c584ad4__section_lj5_zsc_dxb"/>

## Remarks

Used for data extraction from data lake Relational Engine to either a data lake Files container, or to Azure Blob storage, or to an Amazon S3 bucket.

Azure block blobs have a size limit of 4.75 TB. Amazon S3 objects have a size limit of 5 TB. If your extraction exceeds these limits, then you require multiple output files. Use TEMP\_EXTRACT\_NAME*<N\>* if the size limit in TEMP\_EXTRACT\_NAME1 is too small for the amount of data you're extracting.

Files must be smaller than the Azure and Amazon S3 limits. For example, if you're extracting 16 TB to Azure Blob storage, you define four files: TEMP\_EXTRACT\_NAME1, TEMP\_EXTRACT\_NAME2, and TEMP\_EXTRACT\_NAME3 of 4.75 TB each, and TEMP\_EXTRACT\_NAME4 with 1.75 TB.

At the end of your data extraction SELECT statement, set TEMP\_EXTRACT\_NAME*<N\>* to an empty string. If you don't disable, then the next SELECT statement overwrites the object in cloud storage.

For example syntax, see *Extract Data Lake Relational Engine Table Data to Azure Blob Storage* and *Extract Data Lake Relational Engine Table Data to an Amazon S3 Bucket*.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-sap-hana-db-22fc37e.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_CONNECTION\_STRING Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-connection-string-option-deprecated-for-data-lake-relational-engine-sap-hana-102fce6.md "Specifies the connection string of your Azure storage account.")

[TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-name-n-option-for-data-lake-relational-engine-sap-hana-db-managed-1f0b3e1.md)

[TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-region-option-deprecated-for-data-lake-relational-engine-sap-hana-db-managed-38858a2.md "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.")

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-sap-hana-64f7adf.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_SIZE&lt;N&gt; Options for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a6615dd384f21015ae14fe398b6f6188.html "Specifies the maximum sizes of the corresponding output files used by the data extraction facility.") :arrow_upper_right:

