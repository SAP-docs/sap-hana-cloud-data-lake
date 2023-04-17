<!-- loio1f0b3e1f87c948fd881490465f5eea24 -->

# TEMP\_EXTRACT\_NAME<N\> Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio1f0b3e1f87c948fd881490465f5eea24__section_kwq_gzh_mrb"/>

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




<a name="loio1f0b3e1f87c948fd881490465f5eea24__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_ACCESS\_KEY\_ID Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-access-key-id-option-deprecated-for-data-lake-relational-engine-sap-hana-db-22fc37e.md "Supplies the AWS access key. You must specify the access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[TEMP\_EXTRACT\_CONNECTION\_STRING Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-connection-string-option-deprecated-for-data-lake-relational-engine-sap-hana-102fce6.md "Specifies the connection string of your Azure storage account.")

[TEMP\_EXTRACT\_REGION Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-region-option-deprecated-for-data-lake-relational-engine-sap-hana-db-managed-38858a2.md "Specifies the AWS region where your Amazon S3 bucket resides. You must specify the region when extracting data from the Amazon S3 bucket.")

[TEMP\_EXTRACT\_SECRET\_ACCESS\_KEY Option \(Deprecated\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](temp-extract-secret-access-key-option-deprecated-for-data-lake-relational-engine-sap-hana-64f7adf.md "Supplies the AWS secret access key. You must specify the secret access key when extracting data from data lake Relational Engine to an Amazon S3 bucket.")

[(Deprecated) Extract Table Data from Data Lake Relational Engine to Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/72f882141a704328a7ff18c7b0b1914e.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more block blobs in an Azure storage account container.") :arrow_upper_right:

[(Deprecated) Extract Table Data from Data Lake Relational Engine to an Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/5389c53044504f4b9c5865c8f9366ebe.html "Use data lake Relational Engine TEMP_EXTRACT database options in your extraction query to extract data lake Relational Engine data to one or more objects in an Amazon S3 bucket.") :arrow_upper_right:

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[TEMP_EXTRACT_NAME&lt;N&gt; Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a65dd19984f21015ae79a8e590956ad0.html "Specifies the data lake Filescontainer object file name, or theAzure block blob name, or the Amazon S3 bucket object name you’re extracting to. You must specify the name when extracting data from data lake Relational Engine to cloud storage.") :arrow_upper_right:

