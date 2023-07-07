<!-- loio825d3abe4fad45fa82d7619871808c6a -->

# BACKUP TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Backup data lake Relational Engine tables.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
BACKUP TABLE <schema-name>.<table_name> TO <location> 
   [WITH COMPRESSION <value>]
   KEY <encryption_key>
   CONNECTION_STRING <connection_string>
   MAX PART SIZE <integer> BYTES|KB|MB|GB|TB
   MAX PART WRITERS <integer>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio825d3abe4fad45fa82d7619871808c6a__section_c5y_kz2_1rb"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Name of the data lake Relational Engine table you want to backup.



</dd><dt><b>

*<location\>*

</b></dt>
<dd>

Location where the table backup dump will be created in the relevant object store. It is formatted as follows:

-   data lake Files container

    <code>hdlfs:///<i class="varname">&lt;backup-prefix&gt;</i></code>

-   Azure Blob Storage

    <code>bb://<i class="varname">&lt;container-name&gt;</i>/<i class="varname">&lt;backup-prefix&gt;</i></code>

-   Amazon S3 bucketand S3-compliant providers, such as SAP Converged Cloud

    <code>s3://<i class="varname">&lt;bucket-name&gt;</i>/<i class="varname">&lt;backup-prefix&gt;</i></code>

-   Google Cloud Storage

    <code>gs://<i class="varname">&lt;bucket-name&gt;</i>/<i class="varname">&lt;backup-prefix&gt;</i></code>




</dd><dt><b>

*<value\>*

</b></dt>
<dd>

The degree of table compression. Values range between 0 \(minimum\) to 9 \(maximum; both inclusive\). If <code>'[WITH COMPRESSION <i class="varname">&lt;value&gt;</i>'</code> is not specified, default value of 1 is used.



</dd><dt><b>

*<encryption\_key\>*

</b></dt>
<dd>

The encryption key to encrypt the table backup file. Supplying an encryption key is mandatory – you cannot perform a table backup or restore without it.



</dd><dt><b>

CONNECTION\_STRING *<connection\_string\>*

</b></dt>
<dd>

Connection information for the object store in use:

```
<connection_string> ::= 
   { <azure_connection> 
   | <s3_connection>
   | <google_connection> }
```

***<azure\_connection\>***

```
<azure_connection> ::= 'DEFAULTENDPOINTSPROTOCOL=<endpoint_protocol>;
	ACCOUNTNAME=<account_name>;
	ACCOUNTKEY=<account_key>;
	ENDPOINTSUFFIX=core.windows.net'
```

Find your *<azure\_connection\_string\>*, including the access keys from your storage account, in the Azure portal. Locate the *Connection string* section and copy the connection string to the clipboard.

***<google\_connection\>***

```
<google_connection> ::= 'CLIENT_EMAIL='<client_email>';
	PRIVATE_KEY='<private_key>';
     PRIVATE_KEY_ID='<private_key_id>'
```

Find your *<google\_connection\_string\>* comprising the fields *<client\_email\>*, *<private\_key\>*, *<private\_key\_id\>* in the Google Cloud Storage Platform console on the *Service Accounts* page.

***<s3\_connection\>***

```
<s3_connection> ::= 'ENDPOINT=<endpoint>; 
	ENDPOINT_TYPE={PATH | VIRTUAL_HOST}; 
	ACCESS_KEY_ID=<access key string>; 
	SECRET_ACCESS_KEY=<secret key string>; 
	REGION=<region string>; 
	SESSION_TOKEN=<session token>'
```

Find your Amazon S3 option values in the AWS Management Console.

For Amazon S3 and any S3-compliant storage providers, such as SAP Converged Cloud, specify the following options for the *<connection\_string\>* clause:


<dl>
<dt><b>

ENDPOINT

</b></dt>
<dd>

\(Optional for Amazon S3, mandatory for other S3-compliant providers\) When specified for Amazon S3 connections, the Amazon S3 client SDK uses its value as the endpoint to override. You can use this instead of REGION. If both this and the REGION option are specified, the value for REGION needs to be consistent with the value for ENDPOINT.



</dd>
<dd>

If a value is not specified for Amazon S3, the endpoint is determined by the Amazon S3 client SDK and you need to specify a value for the REGION option.



</dd>
</dl>


<dl>
<dt><b>

ENDPOINT\_TYPE

</b></dt>
<dd>

\(Only specify if ENDPOINT is defined\) Indicates how to construct the S3 endpoint when communicating with the object store provider. Values accepted are PATH or VIRTUAL\_HOST. If PATH is specified, Amazon S3 client SDK will construct a path-styled endpoint. If VIRTUAL\_HOST is specified, the Amazon S3 client SDK will construct a virtual-styled endpoint.



</dd>
<dd>

Default value is VIRTUAL\_HOST.



</dd>
</dl>


<dl>
<dt><b>

ACCESS\_KEY\_ID

</b></dt>
<dd>

\(Mandatory\) For Amazon S3, you can find this option value in the AWS Management Console.



</dd>
</dl>


<dl>
<dt><b>

SECRET\_ACCESS\_KEY\_ID

</b></dt>
<dd>

\(Mandatory\) For Amazon S3, you can find this option value in the AWS Management Console.



</dd>
</dl>


<dl>
<dt><b>

REGION

</b></dt>
<dd>

You can use this instead of ENDPOINT for Amazon S3. It allows you to work with Amazon S3 and any S3-compliant data sources.



</dd>
<dd>

If you do not specify this option, the value defaults to server option `iqdl_aws_region` which defaults to `us-east-1`.



</dd>
<dd>

If both this and the ENDPOINT option are specified, the value for REGION needs to be consistent with the value for ENDPOINT.



</dd>
<dd>

If specified, but no value is provided, you are connected to a backend that uses a single server with no concept of regions.



</dd>
</dl>


<dl>
<dt><b>

SESSION\_TOKEN

</b></dt>
<dd>

If specified, the Amazon S3 client SDK will use its value when creating Amazon S3 credentials. If not specified it will be treated as an absence of MFA access for the account.



</dd>
</dl>

***<aws\_connection\>*** \(DEPRECATED\) The following syntax is deprecated as of QRC 2, 2022. Instead, use the syntax above for Amazon S3 and any S3-compliant storage providers.

```

 <aws_connection> ::=
	ACCESS_KEY_ID '<access-key-id>'
	SECRET_ACCESS_KEY '<secret-access-key>' 
	REGION '<AWS-region>'
```

Find your AWS *<access\_key\_id\>*, *<secret\_access\_key\>*, and *<AWS\_region\>* in the AWS Management Console.



</dd><dt><b>

MAX PART SIZE

</b></dt>
<dd>

Specifies the maximum part size to upload when uploading large files to a data lake Files container, Azure Blob Storage, or an Amazon S3 bucket. Files are split into parts up to a maximum number of fragments, uploaded in parallel, and then merged into a single file. The maximum number of fragments for data lake Files and Azure is 50,000, and for Amazon S3 is 10,000.

For example, if the part size value is 10 MB in data lake Files, the maximum size of the uploaded file is 500 GB \(10 x 50,000\). By breaking it into parts, the upload is more efficient. SAP recommends keeping the part size lower to keep operation retry costs down.

For Azure and Amazon S3, the minimum value is 1 MB and maximum value is 500 MB. For data lake Files, the value must be between 10 MB and 500 MB.

The default value is 10 MB.



</dd><dt><b>

MAX PART WRITERS

</b></dt>
<dd>

Specifies the max number of writer threads when uploading large files to a data lake Files container, Azure Blob Storage, or an Amazon S3 bucket. The minimum value is 1 and maximum value is 40.

The default value is 4.



</dd>
</dl>



<a name="loio825d3abe4fad45fa82d7619871808c6a__section_dbx_mz2_1rb"/>

## Remarks

-   The table level backup functionality creates a binary format page image dump of the File Processing index \(as data\) for all the columns in a data lake Relational Engine table.

-   Data lake Relational Engine table backups can be restored to the same or a different table in the same or a different database if they satisfy the following conditions:

    -   The schema of the table being backed up and the one being restored to must be an exact match, however, column names can be different.

    -   The table being restored to must be empty.

    -   The target database has the same page size.


-   Secondary indexes are not backed up and hence not restored – only data as stored in the FP index is restored. While executing a table restore, secondary indexes must not be present. Manually recreate secondary indexes after the table restore is finished.
-   Table level restore doesn't work for tables that have candidate keys involved in a foreign key relationship with itself or any other table.
-   Data lake Relational Engine table backups are always encrypted using the AES256 encryption specification. The encryption key is required while performing a table backup or restore – without the encryption key the restore fails. For enhanced security, encryption is mandatory for table backup and restore to native cloud stores.
-   Data lake Relational Engine ignores the CHECK constraint defined on the table you're restoring a backup to – values are restored irrespective of the constraint.
-   If you back up a table that has a primary key defined on it, restoring that back up requires that no primary keys are defined on the table. However, you must declare those columns \(with a primary key\) as "NOT NULL", else the restore fails. To understand this better, see the following example:

    > ### Example:  
    > ```
    > CREATE TABLE table_1 (ID integer PRIMARY KEY, Name varchar(20));
    >     LOAD TABLE table_1 FROM "table_1_data.tbl";
    >     BACKUP TABLE table_1 TO 's3://<bucket-name>/table_1_backup' 
    >     CONNECTION_STRING 'ACCESS_KEY_ID=assdcjaskj;
    >     SECRET_ACCESS_KEY=regjfkj;
    >     REGION=eu-central-1;
    >     SESSION_TOKEN=FwoGZXIvYXdzECcaD' 
    >     KEY 'abc123'
    >     CREATE TABLE table_2 (ID integer, Name varchar(20));
    >     RESTORE TABLE table_2 from 's3://<bucket-name>/table_1_backup' 
    >     CONNECTION_STRING 'ACCESS_KEY_ID=kgg;
    >         SECRET_ACCESS_KEY=fghvghvgh;
    >         REGION=eu-central-1;
    >         SESSION_TOKEN=FwoGZXIvYXdzECcaD' 
    >     KEY 'abc123'
    > ```
    > 
    > In this example, the RESTORE TABLE statement returns an error.
    > 
    > This happens because the table-level backup/restore logic in data lake Relational Engine checks for a column nullness match, that is, the nullness of all columns between the backed-up table and the restoring table must match. Defining the primary key implicitly also makes that column "NOT NULL". Thus, even if you remove the primary key on the restoring table’s column, it still needs to be "NOT NULL".
    > 
    > To avoid running into such situations, define `TABLE_2` as follows \(add "`NOT NULL`" to the statement\) to ensure that the restore is successful –
    > 
    > ```
    > CREATE TABLE TABLE_2 
    > 	(ID INTEGER NOT NULL, NAME VARCHAR(20))
    > ```




<a name="loio825d3abe4fad45fa82d7619871808c6a__section_nvq_qlr_wwb"/>

## Privileges



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio825d3abe4fad45fa82d7619871808c6a__section_v1r_vz2_1rb"/>

## Security and Encryption

Data lake Relational Engine table backups are encrypted using the AES256 encryption specification. An encryption key is required while taking table backups and performing restores.

> ### Note:  
> For enhanced security, encryption is mandatory for table backup and restore to native cloud stores.



<a name="loio825d3abe4fad45fa82d7619871808c6a__section_yxd_wz2_1rb"/>

## Examples

**Data Lake Files**

```
BACKUP TABLE HDL_T100 TO
    'hdlfs:///hdl_folder/T100_backup'
    WITH COMPRESSION 3
    KEY 'abc123';
```

**Data Lake Files**

```
BACKUP TABLE HDL_T100 TO
    'hdlfs:///hdl_folder/T100_backup'
    WITH COMPRESSION 3
    KEY 'abc123'
    MAX PART SIZE 20
    MAX PART WRITERS 5;
```

**Azure Blob Storage**

```
BACKUP TABLE HDL_T101 TO
    'bb://sap-hanadatalake/hdl_folder'
    CONNECTION_STRING 'DefaultEndpointsProtocol=https;
        AccountName=asdfgsdhbdfs;
        AccountKey=QcaBlsnwirndszDtzo9Mup5b2nejUscdscdsVvZGZpM1ZpJ/WCxtCbxETlRMsE1 Lzo3A==;
        EndpointSuffix=core.windows.net'
    KEY 'IMHO666im_o'
    WITH COMPRESSION 7;
```

**Amazon S3 storage**

```
BACKUP TABLE HDL_T2000 TO
    's3://sap-hanadatalake/hdl_folder'
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        REGION=eu-central-1;
        SESSION_TOKEN=FwoGZXIvYXdzECcaD' 
        KEY 'abc123' 
    WITH COMPRESSION 3; 
```

**SAP Converged Cloud \(an S3-compliant provider\) storage**

```
BACKUP TABLE HDL_T2000 TO
    ‘s3://sap-hanadatalake/hdl_folder'
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
        REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap' 
    WITH COMPRESSION 3;
```

**Google Cloud Storage**

```
BACKUP TABLE original_table TO 
    'gs://SAP_test/testcase_1' 
    CONNECTION_STRING 'client_email=xxx;
        private_key=yyy;
        private_key_id=zzz'
    WITH COMPRESSION 1 key 'abc123DEF!@#$%^&*()'
```

\(DEPRECATED\) The following syntax was used for Amazon S3 and is deprecated as of QRC 2, 2022. Use the syntax above for **Amazon S3 and any S3-compliant providers** instead.

```
BACKUP TABLE HDL_T2000 TO
    's3://sap-hanadatalake/hdl_folder'
    REGION 'us-east-1'
    ACCESS_KEY_ID 'ftwbaebtwjomo'
    SECRET_ACCESS_KEY 'fomoicymiimhoidc'
    KEY 'abc123'
    WITH COMPRESSION 3;
```

**Related Information**  


[RESTORE TABLE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](restore-table-statement-for-data-lake-relational-engine-sap-hana-db-managed-1128b04.md "Restore backed up tables in data lake Relational Engine.")

[Table-Level Backup and Restore of Data in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/5483df1be61442c18d65e0ee66fe27a1.html "Data lake Relational Engine provides table-level backup and restore functionality that enables you to backup and restore individual tables by creating an image of data (FP index in binary format) for all columns in a data lake Relational Engine table.") :arrow_upper_right:

[BACKUP TABLE Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/5c2f08fec3194c57ae23a640fc0cf73f.html "Backup data lake Relational Engine tables.") :arrow_upper_right:

