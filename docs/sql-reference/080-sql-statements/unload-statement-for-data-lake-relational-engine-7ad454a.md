<!-- loio7ad454a70dc84dbfbdfb2513e415fcd2 -->

# UNLOAD Statement for Data Lake Relational Engine

Exports data from data lake Relational Engine to either the external object store \(Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, Google Cloud Storage\) or to data lake Files containers \(the managed object store\).



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio7ad454a70dc84dbfbdfb2513e415fcd2__unload_refsyn1"/>

## Syntax

```
UNLOAD <data-source> <data-target> [ <unload-option> ... ] 

<data-source> ::=  
   { <select-statement> 
   | [ FROM ] TABLE [ { [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <schema-name> (varname] }.]<table-name> }
 
<data-target> ::=  
   { TO <filename>
   | INTO FILE <filename>
   | INTO CLIENT FILE <client-filename> } 

<filename> ::=
    { <filename-pattern> | <string> | <variable> }

<filename-pattern> ::= <a string that contains a '^' character> 

<unload-option> ::= 
   { ACCESS_KEY_ID <string>  
   | SECRET_ACCESS_KEY <string>  
   | REGION <string>
   | BYTE ORDER MARK { ON | OFF }  
   | CONNECTION_STRING <connection_string>  
   | DELIMITED BY <string>  
   | ENCODING <encoding>  
   | { ENCRYPTED KEY '<key>' [ ALGORITHM '<algorithm>' ] | NOT ENCRYPTED }  
   | ESCAPES { ON | OFF }  
   | FORMAT { TEXT | BINARY [ PREFIX( <length> )[ VARYING ] ] [ SWAP ] } 
   | MAX FILE SIZE <size> 
   | MAX PARALLEL DEGREE <integer>
   | MAX PART SIZE [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <integer> (varname] BYTES|KB|MB
   | MAX PART WRITERS [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <integer> (varname] 
   | NULL FORMAT [ { EMPTY | ZEROS } ] 
   | QUOTE <string>  
   | QUOTES { ON | OFF | ALL }  
   | ROW DELIMITED BY <string> } 

<encoding> ::= <string>  

<algorithm> ::=
   { 'AES' 
   | 'AES256'
   | 'AES_FIPS' 
   | 'AES256_FIPS' }
```



<a name="loio7ad454a70dc84dbfbdfb2513e415fcd2__unload_parameters1"/>

## Parameters

 *<data-source\>*:
 :   Specifies the source of the data that will be output. The entire contents of a table can be unloaded, or a select statement can be used if more flexibility is needed.

 :    *<select-statement\>*
 :   The UNLOAD select-statement statement allows data from a SELECT statement to be exported to a file. The result set is not ordered unless the SELECT statement contains an ORDER BY clause.

    If SKIP or LIMIT is used in the SELECT statement, only a single thread will be used to unload the data, whether or not a filename-pattern is specified.

  \[ FROM \] \[ TABLE \] \[ *<owner\>*.\]*<table-name\>*
 :   The UNLOAD TABLE statement allows efficient mass exporting from an entire database table \(or materialized view\) into a file.

    The UNLOAD TABLE statement is more efficient than using the equivalent *<select-statement\>*: '<code>SELECT * FROM [<i class="varname">&lt;owner&gt;</i>.]<i class="varname">&lt;table-name&gt;</i></code>'.

   *<data-target\>*:
 :   Specifies where the unloaded data should be stored.

     TO clause
     :   The *<filename\>* or *<filename-pattern\>* to unload data into. The filename path either specifies a data store URL or is relative to the database server's starting directory. If the file does not exist, it is created. If it already exists, it is overwritten.

        If a server filename is specified, the database server must have operating system permissions to write to the specified file.

      INTO FILE clause
     :   Semantically equivalent to TO `filename`.

      INTO CLIENT FILE clause
     :   The file on the client computer into which the data is unloaded. If the file doesn't exist, it is created. If it already exists, it is overwritten. The path is resolved on the client computer relative to the current working directory of the client application.

        The client application must have operating system permissions to write to the specified file. INTO CLIENT FILE is not supported for Tabular Data Stream \(TDS\) connections.

        UNLOAD TABLE places an exclusive lock on the whole table or materialized view.

      *<filename\>*:
     :   Specifies the name and location of the single file that will contain the unloaded data. Use this parameter if the amount of data to be unloaded is relatively small.

     :   The *<filename\>* prefix specifies the type of data store you're targetting:

        -   ***hdlfs:///*** - write to data lake Files

        -   ***bb://*** - write to Azure BLOB storage

        -   ***s3://*** - write to an Amazon S3 bucketor S3-compliant bucket, such as SAP Converged Cloud

        -   ***gs://*** - write to a Google Cloud Storage bucket


      *<filename-pattern\>*:
     :   Use this parameter if the amount of data to be unloaded is relatively large, and unloading to multiple files is advantageous. The *<filename-pattern\>* is a filename that contains a '^' character, and specifies that multiple files should be used to store the output. The ‘^’ character is a template that constructs the names and locations of the multiple files that will contain the unloaded data.

     :   There are two situations where it's desirable, or necessary, to produce multiple output files:

        -   The output of the UNLOAD statement is larger than the maximum file size for the data store. The MAX FILE SIZE option specifies the maximum size of a file or object. The UNLOAD statement creates as many output files as necessary to store the output in files smaller than the specified maximum size.

        -   To increase the speed of the UNLOAD by using multiple threads to output the data to separate files in parallel. The MAX PARALLEL DEGREE option specifies the maximum number of threads to use for writing data. The MAX FILE SIZE option can also be used to limit the size of files when you're using parallel extraction.


     :   In these two situations, data lake Relational Engine replaces the '^' character in the filename with an identifier to construct the output filename. The '^' character is replaced with '*<thread\_ID\>*\_*<filecount\>*' where each thread has its own ID starting at the value '1'; the filecount starts at 1 and gets incremented as each new file is written.

     :   The UNLOAD statement generates a file listing all the created files. The name of this file is the *<filename-pattern\>* with the '^' character replaced by "***extractinfo***".

     :   You can also unload into the cloud storage of the client, if INTO CLIENT FILE is specified.

     :   If the filename or filename-pattern ends with "gz" or "gzip", the output gets compressed using the gzip format. The default level of compression is 6, but you can set it to a different value between 1 and 9 using the [TEMP\_EXTRACT\_GZ\_COMPRESSION\_LEVEL Option for Data Lake Relational Engine](../090-database-options/temp-extract-gz-compression-level-option-for-data-lake-relational-engine-ee9f6aa.md).

   *<unload-option\>*:
 :   The following options are supported:

     ACCESS\_KEY\_ID *<string\>* 
     :   \(Deprecated as of QRC 2, 2022; use **CONNECTION\_STRING** instead\) 

      SECRET\_ACCESS\_KEY *<string\>* 
     :   \(Deprecated as of QRC 2, 2022; use **CONNECTION\_STRING** instead\) 

      REGION *<string\>* 
     :   \(Deprecated as of QRC 2, 2022; use **CONNECTION\_STRING** instead\) 

      BYTE ORDER MARK \{ ON | OFF \}
     :   Use this clause to specify whether a byte order mark \(BOM\) should be written. When the BYTE ORDER MARK option is ON and the ENCODING is UTF-8 or UTF-16, then a BOM is written. If BYTE ORDER MARK is OFF, a BOM is not unloaded. By default, this option is OFF.

      CONNECTION\_STRING *<connection\_string\>* 
     :   The credentials required to write to Azure BLOB storage, Amazon S3 or S3-compliant storage,and Google Cloud Storage.

     :   ```
<connection_string> ::= 
   { <azure_connection> 
   | <s3_connection>  
   | <google_connection>}
```

         *<azure\_connection\>*
         :   ENCRYPTED KEY

            ```
            <azure_connection> ::= 'DEFAULTENDPOINTSPROTOCOL=<endpoint_protocol>;
            	ACCOUNTNAME=<account_name>;
            	ACCOUNTKEY=<account_key>;
            	ENDPOINTSUFFIX=core.windows.net'
            ```

            You can find the *<azure\_connection\_string\>* values in the Azure portal. From your storage account, navigate to *Settings* \> *Access Keys*. Locate the *Connection string* section and copy the connection string to the clipboard. For *<azure\_connection\_string\>* examples, see the *Examples* section at the end of this topic.

          *<s3\_connection\>*
         :   ```
<s3_connection> ::= 'ENDPOINT=<endpoint>; 
	ENDPOINT_TYPE={PATH | VIRTUAL_HOST}; 
	ACCESS_KEY_ID=<access key string>; 
	SECRET_ACCESS_KEY=<secret key string>; 
	REGION=<region string>; 
	SESSION_TOKEN=<session token>'
```

            You can find your Amazon S3 option values in the AWS Management Console.

            For Amazon S3 and any S3-compliant storage providers, such as SAP Converged Cloud, specify the following options for the *<connection\_string\>* clause:

             ENDPOINT
             :   \(Optional for Amazon S3, mandatory for other S3-compliant providers\) When specified for Amazon S3 connections, the Amazon S3 client SDK uses its value as the endpoint to override. You can use this instead of REGION. If both this and the REGION option are specified, the value for REGION needs to be consistent with the value for ENDPOINT.

             :   If a value is not specified for Amazon S3, the endpoint is determined by the Amazon S3 client SDK and you need to specify a value for the REGION option.

              ENDPOINT\_TYPE
             :   \(Only specify if ENDPOINT is defined\) Indicates how to construct the S3 endpoint when communicating with the object store provider. Values accepted are PATH or VIRTUAL\_HOST. If PATH is specified, Amazon S3 client SDK will construct a path-styled endpoint. If VIRTUAL\_HOST is specified, the Amazon S3 client SDK will construct a virtual-styled endpoint.

             :   Default value is VIRTUAL\_HOST.

              ACCESS\_KEY\_ID
             :   \(Mandatory\) For Amazon S3, you can find this option value in the AWS Management Console.

              SECRET\_ACCESS\_KEY\_ID
             :   \(Mandatory\) For Amazon S3, you can find this option value in the AWS Management Console.

              REGION
             :   You can use this instead of ENDPOINT for Amazon S3. It allows you to work with Amazon S3 and any S3-compliant data sources.

             :   If you do not specify this option, the value defaults to server option `iqdl_aws_region` which defaults to `us-east-1`.

             :   If both this and the ENDPOINT option are specified, the value for REGION needs to be consistent with the value for ENDPOINT.

             :   If specified, but no value is provided, you are connected to a backend that uses a single server with no concept of regions.

              SESSION\_TOKEN
             :   If specified, the Amazon S3 client SDK will use its value when creating Amazon S3 credentials. If not specified it will be treated as an absence of MFA access for the account.

           *<aws\_connection\>*
         \(DEPRECATED\) The following syntax is deprecated as of QRC 2, 2022. Instead, use the syntax above for Amazon S3 and any S3-compliant storage providers.
         :   ```

 <aws_connection> ::=
	ACCESS_KEY_ID '<access_key_id>'
	SECRET_ACCESS_KEY '<secret_access_key>' 
	REGION '<AWS_region>'
```

            You can find *<access\_key\_id\>*, *<secret\_access\_key\>*, and *<AWS\_region\>* in the IAM console. For *<aws\_connection\>* examples, see the *Examples* section at the end of this topic.

          *<google\_connection\>*
         :   ```
<google_connection> ::= 'CLIENT_EMAIL='<client_email>';
	PRIVATE_KEY='<private_key>';
     PRIVATE_KEY_ID='<private_key_id>'
```

            You can find your *<google\_connection\>* keys in Google Cloud Console, on the *Service Accounts* page. *<google\_connection\>* accepts ‘key=value’ pairs separated by ‘;’. For *<google\_connection\>* examples, see the *Examples* section at the end of this topic.

       DELIMITED BY *<string\>* 
     :   The string used to indicate the end of a column. The default column delimiter is a comma. Specify an alternative column delimiter by providing a string up to 4 bytes in length. This option is ignored for BINARY extractions.

     :   If this option is set to an empty string for ASCII extractions, the extracted data is written in fixed-width ASCII with no column delimiter. Numeric and binary data types are right-justified on a field of <n\> blanks, where <n\> is the maximum number of bytes needed for any value of that type. Character data types are left-justified on a field of <n\> blanks.

     :   > ### Note:  
> The minimum column width in a fixed-width ASCII extraction is four bytes to allow the string "NULL" for a NULL value. For example, if the extracted column is CHAR\(2\) and TEMP\_EXTRACT\_COLUMN\_DELIMITER is set to the empty string, there are two spaces added after the extracted data.

      ENCODING *<encoding\>* 
     :   All database data is translated from the database character encoding to the specified CHAR or NCHAR encoding. When ENCODING is not specified, the database's CHAR encoding is used. Character set translation is performed first, before compression or encryption is optionally applied. Specify the BYTE ORDER MARK clause to include a byte order mark in the data.

        See [Character Set Encodings in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_1_QRC/en-US/8a8f277561e547b8a4a0fdfc7f7db7f7.html "A complete list of supported character set encodings for SAP HANA Cloud, data lake and their aliases.") :arrow_upper_right: for a complete list of supported character set encodings.

      \{ ENCRYPTED KEY '*<key\>*' \[ ALGORITHM '*<algorithm\>*' \] | NOT ENCRYPTED \}
     :   Specifies whether to encrypt the data. If you specify NOT ENCRYPTED \(the default\), the data is not encrypted. If you specify ENCRYPTED KEY with a key and no algorithm, the data is encrypted using AES128 and the specified key. The key can be either a string or a variable name. If you specify ENCRYPTED KEY with a key and algorithm, the data is encrypted using the specified key and algorithm. You cannot specify the SIMPLE obfuscation algorithm.

     :   Strong encryption is achieved through the use of a 128-bit algorithm and a security key. The data is unreadable and virtually undecipherable without the key. For strong encryption, specify a 128-bit or 256-bit AES algorithm in the KEY clause to specify an encryption key. You should choose a value for your key that is at least 16 characters long, contains a mix of uppercase and lowercase, and includes numbers, letters, and special characters.

     :   If you choose to compress and encrypt the unloaded data, it is compressed first.

      ESCAPES \{ ON | OFF \}
     :   Specifies whether all quotes in fields containing quotes are escaped in the output of the UNLOAD statement, for a FORMAT TEXT extraction. This option is ignored unless QUOTES ON or QUOTES ALL is specified and QUOTES is either the default value, or '"' \(double quotes\).

      FORMAT \{ TEXT | BINARY \[ PREFIX\(*<length\>*\)\[ VARYING \]\] \[ SWAP \] \}
     :   For TEXT extraction, values are converted to strings for output. The default is to mark the end of column values with commas and end the row with a newline on UNIX platforms and with a carriage return/newline pair on Windows platforms. String values are unquoted by default.

        -   The delimiters can be changed with the DELIMITED BY and ROW DELIMITED BY options. The use of quotes to delimit strings is controlled by the QUOTE, QUOTES and ESCAPES options.


     :   For BINARY extraction, produces a file with an overall "binary" format and a per-column "binary with null byte" format.

        -   PREFIX\(length\) specifies that a prefix field of specified length \(byte\) should be produced for each varchar or varbinary column in the generated output file. This allows you to use BINARY PREFIX in a LOAD TABLE statement for a load of binary data for a varchar or varbinary column.

        -   VARYING specifies that only actual data of the varchar or varbinary column without trailing padding should be added to the generated file. This allows you to use BINARY PREFIX VARYING for a varchar or varbinary column in a load of binary data in a LOAD TABLE statement. If VARYING is specified, PREFIX\(length\) must also be specified.

        -   SWAP specifies that the generated output file is designed to be loaded on another machine with opposite endianness.


      MAX FILE SIZE *<size\>*
     :   Specifies the maximum size of the generated output file object, in KB. When you specify MAX FILE SIZE, the UNLOAD statement writes data to as many files as needed so that each file is smaller than the maximum size. A *<filename-pattern\>* must be specified when using MAX FILE SIZE.

        Use this parameter if you want to upload data that is larger than the maximum file size imposed by the object store \(see note below\).

     :   > ### Note:  
> If unloading to the external object store \(Azure BLOB storage, AWS S3 bucket, Google Cloud Storage\), the maximum file size is 5 TB \(5,000,000,000 KB\).
> 
> If unloading to data lake Files, the maximum file size is 1 TB \(1,000,000,000 KB\).

     :   The default value is 0. This converts to the maximum file size: 5 TB for unloads to the external object store; 1 TB for unloads to data lake Files.

     :   > ### Restriction:  
> The MAX FILE SIZE clause is not supported for unloads with compressed output.

      MAX PARALLEL DEGREE *<integer\>*
     :   Specifies the maximum number of threads that will be used to unload data in parallel into multiple files. The server chooses the optimal number of threads to use for unloading, up to the specified maximum. The default value is 64. You need to provide a *<filename-pattern\>* when this option is specified.

      MAX PART SIZE
     :   Specifies the maximum part size to upload when uploading large files to a data lake Files container, Azure Blob Storage, or an Amazon S3 bucket. Files are split into parts up to a maximum number of fragments, uploaded in parallel, and then merged into a single file. The maximum number of fragments for data lake Files and Azure is 50,000, and for Amazon S3 is 10,000.

        For example, if the part size value is 10 MB in data lake Files, the maximum size of the uploaded file is 500 GB \(10 x 50,000\). By breaking it into parts, the upload is more efficient. SAP recommends keeping the part size lower to keep operation retry costs down.

        You can use this parameter along with the MAX FILE SIZE parameter. For example, if you need to upload 10 TB of data in data lake Files, you can set MAX PART SIZE to 20 MB and MAX FILE SIZE to 1 TB. Each object would reach the size of 1 TB \(20 MB x 50,000\) after which a new object would be created as specified by the value of MAX FILE SIZE.

        For Azure and Amazon S3, the minimum value is 1 MB and maximum value is 500 MB. For data lake Files, the value must be between 10 MB and 500 MB.

        The default value is 10 MB.

      MAX PART WRITERS
     :   Specifies the max number of writer threads when uploading large files to a data lake Files container, Azure Blob Storage, or an Amazon S3 bucket. The minimum value is 1 and maximum value is 40.

        The default value is 4.

      NULL FORMAT \[ EMPTY | ZEROS \]
     :   Controls the representation of null values for ASCII extractions.

        -   With NULL FORMAT ZEROS, a null value is represented as '0' for arithmetic types and '' \(the empty string\) for all other types.

        -   With NULL FORMAT EMPTY, a null value is represented as '' \(the empty string\) for all data types.

        -   When there is no NULL FORMAT option \(the default\), the string 'NULL' is used in all cases to represent a NULL value.


        > ### Note:  
        > The quotation marks shown here are not present in the extract output file.

     :   If NULL FORMAT ZEROS is specified, the number of characters that an ASCII extract writes to a file for a CHAR or VARCHAR column equals the number of characters in the column, even if that number is fewer than four.

      QUOTE *<string\>* 
     :   Specifies the string to be used as the quote to enclose fields in the output of the data extraction facility for an ASCII extraction, when either the QUOTES ON or QUOTES ALL option is set. The default for this option is the empty string, which data lake Relational Engine converts to the single quote mark. The string specified in the QUOTE option must occupy from 1 to a maximum of 4 bytes and must be valid in the collation order you are using, if you are using a multibyte collation order. Be sure to choose a string that does not occur in any of the data output strings themselves.

      QUOTES \{ ON | OFF | ALL \}
     :   Specifies whether output values should be enclosed in quotes in FORMAT TEXT files.

     :   -   QUOTES ON specifies that string fields should be enclosed in quotes.

-   QUOTES ALL specifies that all fields should be enclosed in quotes.

-   QUOTES OFF, the default, specifies that quotes should not be used.


     :   By default, a single quote character "'" is used, but this can be changed with the QUOTE option.

      ROW DELIMITED BY *<string\>* 
     :   Specifies the delimiter that marks the ends of rows in the output of the data extraction facility for a FORMAT TEXT extraction. The delimiter must occupy 1 to 4 bytes and must be valid in the collation order you are using, if you are using a multibyte collation order. Choose a delimiter that does not occur in any of the data output strings. The default value for this option is the empty string.

  

<a name="loio7ad454a70dc84dbfbdfb2513e415fcd2__unload_remarks1"/>

## Remarks

If you unload data in binary format, and then use the LOAD TABLE statement to read the unloaded data, you'll need to use the BINARY WITH NULL BYTE parameter for each column.

The *<filename\>* or *<filename-pattern\>* parameter is a URL that specifies the location and names of the files that will contain the unloaded data. If the amount of data to be unloaded is relatively small, the *<filename\>* parameter identifies the single file or object that will be written. If the amount of data to be unloaded is large, it may be necessary or advantageous to use multiple files to store the output, in which case a *<filename-pattern\>* can be specified that is used as a template to construct the names of the multiple output files.

The ENCODING and BYTE ORDER MARK can only be used with FORMAT TEXT.

The UNLOAD statement determines whether the specified files are compressed by looking for a `.gz` or `.gzip` suffix.

If writing files to a client machine, you must use either the ODBC or JDBC iAnywhere drivers.

The UNLOAD statement supports SQL Anywhere and data lake Relational Engine tables. You can’t use the UNLOAD statement on proxy tables.



<a name="loio7ad454a70dc84dbfbdfb2513e415fcd2__unload_privileges1"/>

## Privileges



### 

Unloading data requires one of:

-   You own the table being unloaded
-   You have the SELECT object-level privilege on the tables
-   SELECT ANY TABLE system privilege

Unloading to a file on a client machine requires:

-   WRITE CLIENT FILE system privilege
-   Write permissions on the directory where the file is located
-   The ALLOW\_READ\_CLIENT\_FILE database option is enabled.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio7ad454a70dc84dbfbdfb2513e415fcd2__unload_examples1"/>

## Examples

This example unloads all data in table t1 to the default container in data lake Files, in binary format:

```
UNLOAD SELECT * FROM t1 
    INTO FILE 'hdlfs:///Q3_results.dat'
    FORMAT BINARY
```

This example unloads the entire contents of table t1 to Amazon S3, using compression and parallel extraction \(up to five threads\):

```
UNLOAD FROM TABLE t1 
    INTO FILE 's3://my_S3_data/Q3results^.gz'
    CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
    	SECRET_ACCESS_KEY=abc;
    	REGION=eu-central-1;
    	SESSION_TOKEN=pqr'
    MAX PARALLEL DEGREE 5;
```

This example unloads the entire contents of table t1 to Amazon S3, using compression and parallel extraction \(up to five threads\):

```
UNLOAD FROM TABLE t1 
    INTO FILE 's3://my_S3_data/Q3results^.gz'
    CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
    	SECRET_ACCESS_KEY=abc;
    	REGION=eu-central-1;
    	SESSION_TOKEN=pqr'
    MAX PARALLEL DEGREE 5;
```

This example unloads the entire contents of table t1 to SAP Converged Cloud \(an S3-compliant storage provider\), using compression and parallel extraction \(up to five threads\) with a part size of 10 MB:

```
UNLOAD FROM TABLE t1 
    INTO FILE '‘s3://sap-hanadatalake/hdl_folder/Q3results^.gz'
    CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
    	SECRET_ACCESS_KEY=abc;
    	REGION=eu-central-1;
    	SESSION_TOKEN=pqr'
    MAX PARALLEL DEGREE 5
    MAX PART SIZE 10 MB;
```

This example unloads the entire contents of table t1 to Azure storage, using compression and parallel extraction \(up to five threads\):

```
UNLOAD FROM TABLE t1 
    INTO FILE 'bb://my_azure_data/Q3results^.gz'
    CONNECTION_STRING 'DefaultEndpointsProtocol=https;
    	AccountName=example;
    	AccountKey=example_key;
    	EndpointSuffix=core.windows.net'
    MAX PARALLEL DEGREE 5;
```

This example unloads the entire contents of table t1 to Google Cloud Storage, using compression and parallel extraction \(up to five threads\):

```
UNLOAD FROM TABLE t1 
    INTO FILE 'gs://my_bucket/Q3results^.gz'
    CONNECTION_STRING 'client_email=XXXXXXXX;
    	PRIVATE_KEY=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
    	PRIVATE_KEY_ID=XXXXXXXX'
    MAX PARALLEL DEGREE 5;
```

\(Deprecated\) This example unloads the entire contents of table t1 to S3 storage, using compression and parallel extraction \(up to five threads\):

```
UNLOAD FROM TABLE t1 
    INTO FILE 's3://my_S3_data/Q3results^.gz'
    ACCESS_KEY_ID 'XXXXXXXXXXXXXXXXXXXX'
    SECRET_ACCESS_KEY 'XXXXXXXXXXXXXXXXXXXX/XXXXXX/XXXXXXXXX'
    REGION 'us-east-2'
    MAX PARALLEL DEGREE 5;
```

**Related Information**  


[UNLOAD Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/5049a399ee2241dda78d47a0a3cc46e9.html "Exports data from data lake Relational Engine to either the external object store (Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, Google Cloud Storage) or to data lake Files containers (the managed object store).") :arrow_upper_right:

[SAP HANA Cloud, Data Lake Load and Unload Management](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/e77c96193a604e05ba198e424de2ed6c.html "Data load (import) and export (unload) procedures for data lake Relational Engine, including loading from and unloading to data lake Files.") :arrow_upper_right:

[Unloading Data to the External Object Store](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/31a19ffdd4af430c8ebc962cbac2cf5a.html "Unload (extract) data from data lake Relational Engine to the external object store using either the UNLOAD statement, or the data extraction facility.") :arrow_upper_right:

[Unloading Data to Data Lake Files from Data Lake Relational Engine](https://help.sap.com/viewer/b239ed4bb73a4f07886657e237f1875f/2023_1_QRC/en-US/128c5bced169487f98eb2e2a49e7fd45.html "Use the UNLOAD statement to unload data to data lake Files.") :arrow_upper_right:

[TEMP\_EXTRACT\_GZ\_COMPRESSION\_LEVEL Option for Data Lake Relational Engine](../090-database-options/temp-extract-gz-compression-level-option-for-data-lake-relational-engine-ee9f6aa.md "The compression level balances compression with speed when the TEMP_EXTRACT_COMPRESS option is set to ON.")

[SAP HANA Cloud, Data Lake Terminology](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_1_QRC/en-US/d003004765fb4475b14d83e5c51b117f.html "Definitions of data lake terms used in this document.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

