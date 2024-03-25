<!-- loio5049a399ee2241dda78d47a0a3cc46e9 -->

# UNLOAD Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Exports data from data lake Relational Engine to either the external object store \(Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, Google Cloud Storage\) or to data lake Files containers \(the managed object store\).



<a name="loio5049a399ee2241dda78d47a0a3cc46e9__section_p53_lcs_s4b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



<a name="loio5049a399ee2241dda78d47a0a3cc46e9__section_egm_35w_brb"/>

## Syntax

```
UNLOAD <data-source> <data-target> [ <unload-option> ... ] 

<data-source> ::=  
   { <select-statement> 
   | [ FROM ] TABLE [ <schema-name>.]<table-name> }

<data-target> ::=  
   { TO <filename>
   | INTO FILE <filename>
   | INTO CLIENT FILE <client-filename> } 

<filename> ::= { <filename-pattern> | <string> | <variable> }

<filename-pattern> ::= <a string that contains a '^' character> 

<unload-option> ::= 
   { ACCESS_KEY_ID <string>  
   | SECRET_ACCESS_KEY <string>  
   | REGION <string>
   | BYTE ORDER MARK { ON | OFF }  
   | CONNECTION_STRING <connection_string>
   | WITH CREDENTIAL <purpose-def>
   | DELIMITED BY <string>  
   | ENCODING <encoding>  
   | { ENCRYPTED KEY '<key>' [ ALGORITHM '<algorithm>' ] | NOT ENCRYPTED }  
   | ESCAPES { ON | OFF }  l
   | FORMAT { PARQUET | TEXT | BINARY [ PREFIX( <length> ) [ VARYING ] ] [ SWAP ] } 
   | MAX FILE SIZE <size> 
   | MAX PARALLEL DEGREE <integer>
   | MAX PART SIZE <integer> [ BYTES | KB | MB ]
   | MAX PART WRITERS <integer>
   | ROW GROUP SIZE <integer>
   | COMPRESSION { SNAPPY | BROTLI | GZIP | LZ4 | ZSTD | NONE } 
   | NULL FORMAT [ { EMPTY | ZEROS } ] 
   | QUOTE <string>  
   | QUOTES { ON | OFF | ALL }  
   | ROW DELIMITED BY <string> } 

<encoding> ::= <string>  

<algorithm> ::= { 'AES' | 'AES256' | 'AES_FIPS' | 'AES256_FIPS' }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio5049a399ee2241dda78d47a0a3cc46e9__section_rtv_j5w_brb"/>

## Parameters



### *<select-statement\>*


<dl>
<dt><b>



</b></dt>
<dd>

The UNLOAD *<select-statement\>* allows data from a SELECT statement to be exported to a file. The result set is not ordered unless the SELECT statement contains an ORDER BY clause.

If SKIP or LIMIT is used in the SELECT statement, only a single thread will be used to unload the data, whether or not a filename-pattern is specified.



</dd>
</dl>



### \[ FROM \] \[ TABLE \] \[ *<owner\>*.\]*<table-name\>*


<dl>
<dt><b>



</b></dt>
<dd>

The UNLOAD TABLE statement allows efficient mass exporting from an entire database table \(or materialized view\) into a file.



</dd>
</dl>



### TO


<dl>
<dt><b>



</b></dt>
<dd>

The *<filename\>* or *<filename-pattern\>* to unload data into. The filename path specifies a data store URL. If the file does not exist, it is created. If it already exists, it is overwritten.



</dd>
</dl>



### INTO FILE


<dl>
<dt><b>



</b></dt>
<dd>

Semantically equivalent to TO `filename`.



</dd>
</dl>



### INTO CLIENT FILE


<dl>
<dt><b>



</b></dt>
<dd>

The file on the client computer into which the data is unloaded. If the file doesn't exist, it is created. If it already exists, it is overwritten. The path is resolved on the client computer relative to the current working directory of the client application.

The client application must have operating system permissions to write to the specified file. INTO CLIENT FILE is not supported for Tabular Data Stream \(TDS\) connections.



</dd>
</dl>



### *<filename\>*:


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the name and location of the single file that will contain the unloaded data. Use this parameter if the amount of data to be unloaded is relatively small.



</dd>
<dd>

The *<filename\>* prefix specifies the type of data store you're targetting:

-   `hdlfs:///` - write to the defaultdata lake Files container

-   `hdlfs://` to write to a non-default container \(one outside of your data lake instance\)

-   `bb://` - write to Azure BLOB storage

-   `s3://` - write to an Amazon S3 bucketor S3-compliant bucket, such as SAP Converged Cloud

-   `gs://` - write to a Google Cloud Storage bucket




</dd>
</dl>



### *<filename-pattern\>*:


<dl>
<dt><b>



</b></dt>
<dd>

Use this parameter if the amount of data to be unloaded is relatively large, and unloading to multiple files is advantageous. The *<filename-pattern\>* is a filename that contains a '^' character, and specifies that multiple files should be used to store the output. The ‘^’ character is a template that constructs the names and locations of the multiple files that will contain the unloaded data.



</dd>
<dd>

There are two situations where it's desirable, or necessary, to produce multiple output files:

-   The output of the UNLOAD statement is larger than the maximum file size for the data store. The MAX FILE SIZE option specifies the maximum size of a file or object. The UNLOAD statement creates as many output files as necessary to store the output in files smaller than the specified maximum size.

-   To increase the speed of the UNLOAD by using multiple threads to output the data to separate files in parallel. The MAX PARALLEL DEGREE option specifies the maximum number of threads to use for writing data. The MAX FILE SIZE option can also be used to limit the size of files when you're using parallel extraction.




</dd>
<dd>

In these two situations, data lake Relational Engine replaces the '^' character in the filename with an identifier to construct the output filename. The '^' character is replaced with '*<thread\_ID\>*\_*<filecount\>*' where each thread has its own ID starting at the value '1'; the filecount starts at 1 and gets incremented as each new file is written by that thread.



</dd>
<dd>

The UNLOAD statement generates a file listing all the created files. The name of this file is the *<filename-pattern\>* with the '^' character replaced by "***extractinfo***".



</dd>
<dd>

You can also unload into the storage of the client, if INTO CLIENT FILE is specified.



</dd>
<dd>

If the filename or filename-pattern ends with "gz" or "gzip", the output gets compressed using the gzip format. The default level of compression is 6, but you can set it to a different value between 1 and 9 using the [TEMP_EXTRACT_GZ_COMPRESSION_LEVEL Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/ee9f6aaf17ec413dad8bd2c998adbf54.html "The compression level balances compression with speed when the TEMP_EXTRACT_COMPRESS option is set to ON.") :arrow_upper_right:.



</dd>
</dl>



### ACCESS\_KEY\_ID *<string\>* 


<dl>
<dt><b>



</b></dt>
<dd>

\(Deprecated as of QRC 2, 2022; use **CONNECTION\_STRING** instead\) 



</dd>
</dl>



### SECRET\_ACCESS\_KEY *<string\>*


<dl>
<dt><b>



</b></dt>
<dd>

\(Deprecated as of QRC 2, 2022; use **CONNECTION\_STRING** instead\) 



</dd>
</dl>



### REGION *<string\>* 


<dl>
<dt><b>



</b></dt>
<dd>

\(Deprecated as of QRC 2, 2022; use **CONNECTION\_STRING** instead\) 



</dd>
</dl>



### BYTE ORDER MARK \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Use this clause to specify whether a byte order mark \(BOM\) should be written. When the BYTE ORDER MARK option is ON and the ENCODING is UTF-8 or UTF-16, then a BOM is written. If BYTE ORDER MARK is OFF, a BOM is not unloaded. By default, this option is OFF.



</dd>
</dl>



### CONNECTION\_STRING *<connection\_string\>*


<dl>
<dt><b>



</b></dt>
<dd>

The credentials required to write to Azure BLOB storage, Amazon S3 or S3-compliant storage,and Google Cloud Storage.



</dd>
<dd>

```
<connection_string> ::= 
   { <non-default-hdlfs-instance> 
   | <azure_connection> 
   | <s3_connection>  
   | <google_connection>};
```


<dl>
<dt><b>

*<non-default-hdlfs-instance\>*

</b></dt>
<dd>

```
<non-default-hdlfs-instance> ::= 'ENDPOINT=<endpoint>;
	CA_CERTIFICATE=<certificate-content>;
	CLIENT_CERTIFICATE=<certificate-content>;
	CLIENT_KEY=<client-certificate-key>;
	KEY_PASSWORD= <certificate_key_password>';
```

This clause is optional for data lake Files containers. If you don't specify it, the UNLOAD statement will connect to the default data lake Files container provisioned within your data lake instance. If you do, the UNLOAD statement can connect to an alternate, non-default data lake Files container within a separate data lake instance.

Specify the following options for the *<connection-string\>* clause:


<dl>
<dt><b>

ENDPOINT

</b></dt>
<dd>

\(Mandatory\) Represents the non-default data lake Files container endpoint. Use 'https://' as a prefix.



</dd><dt><b>

CA\_CERTIFICATE

</b></dt>
<dd>

Specifies the data lake Files server certificate used to verify the connection during SSL handshake. If left blank, it will be picked from the default data lake Files container.



</dd><dt><b>

CLIENT\_CERTIFICATE

</b></dt>
<dd>

\(Not needed if the WITH CREDENTIAL clause is specified\) Specifies the client certificate for the data lake Files container. This certificate may hold the entire chain of certificates. Accepts content in PEM format.



</dd><dt><b>

CLIENT\_KEY

</b></dt>
<dd>

\(Not needed if the WITH CREDENTIAL clause is specified\) Represents a private key. Accepts content in PEM format.



</dd><dt><b>

KEY\_PASSWORD

</b></dt>
<dd>

If specified, this value will be the password used to decrypt the client key. If not specified, and if the CLIENT\_KEY option is specified, it would be assumed to be in unencrypted form.



</dd>
</dl>



</dd><dt><b>

*<azure\_connection\>*

</b></dt>
<dd>

```
<azure_connection> ::= 'DEFAULTENDPOINTSPROTOCOL=<endpoint_protocol>;
	ACCOUNTNAME=<account_name>;
	ACCOUNTKEY=<account_key>;
	ENDPOINTSUFFIX=core.windows.net';
```

You can find the *<azure\_connection\_string\>* values in the Azure portal. From your storage account, navigate to *Settings* \> *Access Keys*. Locate the *Connection string* section and copy the connection string to the clipboard. For *<azure\_connection\_string\>* examples, see the *Examples* section at the end of this topic.



</dd><dt><b>

*<s3\_connection\>*

</b></dt>
<dd>

```
<s3_connection> ::= 'ENDPOINT=<endpoint>; 
	ENDPOINT_TYPE={PATH | VIRTUAL_HOST}; 
	ACCESS_KEY_ID=<access key string>; 
	SECRET_ACCESS_KEY=<secret key string>; 
	REGION=<region string>; 
	SESSION_TOKEN=<session token>';
```

You can find your Amazon S3 option values in the AWS Management Console.

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



</dd><dt><b>

*<aws\_connection\>*\(DEPRECATED\) The following syntax is deprecated as of QRC 2, 2022. Instead, use the syntax above for Amazon S3 and any S3-compliant storage providers.

</b></dt>
<dd>

```

 <aws_connection> ::=
	ACCESS_KEY_ID '<access_key_id>'
	SECRET_ACCESS_KEY '<secret_access_key>' 
	REGION '<AWS_region>';
```

You can find *<access\_key\_id\>*, *<secret\_access\_key\>*, and *<AWS\_region\>* in the IAM console. For *<aws\_connection\>* examples, see the *Examples* section at the end of this topic.



</dd><dt><b>

*<google\_connection\>*

</b></dt>
<dd>

```
<google_connection> ::= 'CLIENT_EMAIL='<client_email>';
	PRIVATE_KEY='<private_key>';
     PRIVATE_KEY_ID='<private_key_id>';
```

You can find your *<google\_connection\>* keys in Google Cloud Console, on the *Service Accounts* page. *<google\_connection\>* accepts ‘key=value’ pairs separated by ‘;’. For *<google\_connection\>* examples, see the *Examples* section at the end of this topic.



</dd>
</dl>



</dd>
</dl>



### WITH CREDENTIAL *<purpose-def\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the name of the credential's purpose as defined in the CREATE CREDENTIAL statement.



</dd>
</dl>



### DELIMITED BY *<string\>* 


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)The string used to indicate the end of a column. The default column delimiter is a comma. Specify an alternative column delimiter by providing a string up to 4 bytes in length. This option is ignored for BINARY extractions.



</dd>
<dd>

If this option is set to an empty string for ASCII extractions, the extracted data is written in fixed-width ASCII with no column delimiter. Numeric and binary data types are right-justified on a field of <n\> blanks, where <n\> is the maximum number of bytes needed for any value of that type. Character data types are left-justified on a field of <n\> blanks.



</dd>
<dd>

> ### Note:  
> The minimum column width in a fixed-width ASCII extraction is four bytes to allow the string "NULL" for a NULL value. For example, if the extracted column is CHAR\(2\) and TEMP\_EXTRACT\_COLUMN\_DELIMITER is set to the empty string, there are two spaces added after the extracted data.



</dd>
</dl>



### ENCODING *<encoding\>* 


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)All database data is translated from the database character encoding to the specified encoding. When ENCODING is not specified, the database's CHAR encoding is used. Character set translation is performed first, before compression or encryption is optionally applied. Specify the BYTE ORDER MARK clause to include a byte order mark in the data.

See [Character Set Encodings in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_1_QRC/en-US/8a8f277561e547b8a4a0fdfc7f7db7f7.html "A complete list of supported character set encodings for SAP HANA Cloud, data lake and their aliases.") :arrow_upper_right: for a complete list of supported character set encodings.



</dd>
</dl>



### \{ ENCRYPTED KEY '*<key\>*' \[ ALGORITHM '*<algorithm\>*' \] | NOT ENCRYPTED \}


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Specifies whether to encrypt the data. If you specify NOT ENCRYPTED \(the default\), the data is not encrypted. If you specify ENCRYPTED KEY with a key and no algorithm, the data is encrypted using AES128 and the specified key. The key can be either a string or a variable name. If you specify ENCRYPTED KEY with a key and algorithm, the data is encrypted using the specified key and algorithm. You cannot specify the SIMPLE obfuscation algorithm.



</dd>
<dd>

Strong encryption is achieved through the use of a 128-bit algorithm and a security key. The data is unreadable and virtually undecipherable without the key. For strong encryption, specify a 128-bit or 256-bit AES algorithm in the KEY clause to specify an encryption key. You should choose a value for your key that is at least 16 characters long, contains a mix of uppercase and lowercase, and includes numbers, letters, and special characters.



</dd>
<dd>

If you choose to compress and encrypt the unloaded data, it is compressed first.



</dd>
</dl>



### ESCAPES \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Specifies whether all quotes in fields containing quotes are escaped in the output of the UNLOAD statement, for a FORMAT TEXT extraction. This option is ignored unless QUOTES ON or QUOTES ALL is specified and QUOTES is either the default value, or '"' \(double quotes\).



</dd>
</dl>



### FORMAT \{ PARQUET |TEXT | BINARY \[ PREFIX\(*<length\>*\)\[ VARYING \]\] \[ SWAP \] \}


<dl>
<dt><b>



</b></dt>
<dd>

-   For TEXT extraction, values are converted to strings for output. The default is to mark the end of column values with commas and end the row with a newline on UNIX platforms and with a carriage return/newline pair on Windows platforms. String values are unquoted by default.

    -   The delimiters can be changed with the DELIMITED BY and ROW DELIMITED BY options. The use of quotes to delimit strings is controlled by the QUOTE, QUOTES and ESCAPES options.


-   For BINARY extraction, produces a file with an overall "binary" format and a per-column "binary with null byte" format.

-   PREFIX\(length\) specifies that a prefix field of specified length \(byte\) should be produced for each varchar or varbinary column in the generated output file. This allows you to use BINARY PREFIX in a LOAD TABLE statement for a load of binary data for a varchar or varbinary column.

-   VARYING specifies that only actual data of the varchar or varbinary column without trailing padding should be added to the generated file. This allows you to use BINARY PREFIX VARYING for a varchar or varbinary column in a load of binary data in a LOAD TABLE statement. If VARYING is specified, PREFIX\(length\) must also be specified.

-   SWAP specifies that the generated output file is designed to be loaded on another machine with opposite endianness.




</dd>
</dl>



### MAX FILE SIZE *<size\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the maximum size of the generated output file object, in KB. When you specify MAX FILE SIZE, the UNLOAD statement writes data to as many files as needed so that each file is smaller than the maximum size. A *<filename-pattern\>* must be specified when using MAX FILE SIZE.

Use this parameter if you want to upload data that is larger than the maximum file size imposed by the object store \(see note below\).



</dd>
<dd>

> ### Note:  
> If unloading to the external object store \(Azure BLOB storage, AWS S3 bucket, Google Cloud Storage\), the maximum file size is 5 TB \(5,000,000,000 KB\).
> 
> If unloading to data lake Files, the maximum file size is 1 TB \(1,000,000,000 KB\).



</dd>
<dd>

The default value is 0. This converts to the maximum file size: 5 TB for unloads to the external object store; 1 TB for unloads to data lake Files.



</dd>
<dd>

> ### Restriction:  
> The MAX FILE SIZE clause is not supported for unloads with compressed output.



</dd>
</dl>



### MAX PARALLEL DEGREE *<integer\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the maximum number of threads that will be used to unload data in parallel into multiple files. The server chooses the optimal number of threads to use for unloading, up to the specified maximum. The default value is 64. You need to provide a *<filename-pattern\>* when this option is specified.



</dd>
</dl>



### MAX PART SIZE


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the maximum part size to upload when uploading large files to a data lake Files container, Azure Blob Storage, or an Amazon S3 bucket. Files are split into parts up to a maximum number of fragments, uploaded in parallel, and then merged into a single file. The maximum number of fragments for data lake Files and Azure is 50,000, and for Amazon S3 is 10,000.

For example, if the part size value is 10 MB in data lake Files, the maximum size of the uploaded file is 500 GB \(10 x 50,000\). By breaking it into parts, the upload is more efficient. SAP recommends keeping the part size lower to keep operation retry costs down.

You can use this parameter along with the MAX FILE SIZE parameter. For example, if you need to upload 10 TB of data in data lake Files, you can set MAX PART SIZE to 20 MB and MAX FILE SIZE to 1 TB. Each object would reach the size of 1 TB \(20 MB x 50,000\) after which a new object would be created as specified by the value of MAX FILE SIZE.

For Azure and Amazon S3, the minimum value is 1 MB and maximum value is 500 MB. For data lake Files, the value must be between 10 MB and 500 MB.

The default value is 10 MB.



</dd>
</dl>



### MAX PART WRITERS


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the max number of writer threads when uploading large files to a data lake Files container, Azure Blob Storage, or an Amazon S3 bucket. The minimum value is 1 and maximum value is 40.

The default value is 4.



</dd>
</dl>



### ROW GROUP SIZE *<integer\>*


<dl>
<dt><b>



</b></dt>
<dd>

\(Only applicable to Parquet format\) Specifies how many rows should be in a rowgroup. Parquet files are split into rowgroups which are segments of the file that are read independently of one another.

If used in combination with the MAX FILE SIZE clause and the maximum file size value is reached, the current rowgroup being written may have fewer rows than the value specified for the ROW GROUP SIZE clause. Depending on the MAX FILE SIZE value, the result can be many files with one or more rowgroups, and a final file with a rowgroup that has less rows than the previous rowgroups.

The default value is 100,000 rows.



</dd>
</dl>



### COMPRESSION \{ SNAPPY | BROTLI | GZIP | LZ4 | ZSTD | NONE \}


<dl>
<dt><b>



</b></dt>
<dd>

\(Only applicable to Parquet format\) Specifies the compression codec to apply when unloading Parquet files.

The default value is SNAPPY.



</dd>
</dl>



### NULL FORMAT \[ EMPTY | ZEROS \]


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Controls the representation of null values for ASCII extractions.

-   With NULL FORMAT ZEROS, a null value is represented as '0' for arithmetic types and '' \(the empty string\) for all other types.

-   With NULL FORMAT EMPTY, a null value is represented as '' \(the empty string\) for all data types.

-   When there is no NULL FORMAT option \(the default\), the string 'NULL' is used in all cases to represent a NULL value.


> ### Note:  
> The quotation marks shown here are not present in the extract output file.



</dd>
<dd>

If NULL FORMAT ZEROS is specified, the number of characters that an ASCII extract writes to a file for a CHAR or VARCHAR column equals the number of characters in the column, even if that number is fewer than four.



</dd>
</dl>



### QUOTE *<string\>*


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Specifies the string to be used as the quote to enclose fields in the output of the data extraction facility for an ASCII extraction, when either the QUOTES ON or QUOTES ALL option is set. The default for this option is the empty string, which data lake Relational Engine converts to the single quote mark. The string specified in the QUOTE option must occupy from 1 to a maximum of 4 bytes and must be valid in the collation order you are using, if you are using a multibyte collation order. Be sure to choose a string that does not occur in any of the data output strings themselves.



</dd>
</dl>



### QUOTES \{ ON | OFF | ALL \}


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Specifies whether output values should be enclosed in quotes in FORMAT TEXT files.



</dd>
<dd>

-   QUOTES ON specifies that string fields should be enclosed in quotes.

-   QUOTES ALL specifies that all fields should be enclosed in quotes.

-   QUOTES OFF, the default, specifies that quotes should not be used.




</dd>
<dd>

By default, a single quote character "'" is used, but this can be changed with the QUOTE option.



</dd>
</dl>



### ROW DELIMITED BY *<string\>* 


<dl>
<dt><b>



</b></dt>
<dd>

\(Not applicable to Parquet format\)Specifies the delimiter that marks the ends of rows in the output of the data extraction facility for a FORMAT TEXT extraction. The delimiter must occupy 1 to 4 bytes and must be valid in the collation order you are using, if you are using a multibyte collation order. Choose a delimiter that does not occur in any of the data output strings. The default value for this option is the empty string.



</dd>
</dl>



<a name="loio5049a399ee2241dda78d47a0a3cc46e9__section_qbr_k5w_brb"/>

## Remarks

If you unload data in binary format, and then use the LOAD TABLE statement to read the unloaded data, you'll need to use the BINARY WITH NULL BYTE parameter for each column.

The *<filename\>* or *<filename-pattern\>* parameter is a URL that specifies the location and names of the files that will contain the unloaded data. If the amount of data to be unloaded is relatively small, the *<filename\>* parameter identifies the single file or object that will be written. If the amount of data to be unloaded is large, it may be necessary or advantageous to use multiple files to store the output, in which case a *<filename-pattern\>* can be specified that is used as a template to construct the names of the multiple output files.

The ENCODING and BYTE ORDER MARK can only be used with FORMAT TEXT.

For non-parquet formats, the UNLOAD statement determines whether the specified files are compressed by looking for a `.gz` or `.gzip` filename suffix. For Parquet format, compression is determined by the value provided in the COMPRESSION clause.

If writing files to a client machine, use one of the data lake Relational Engine client drivers. TDS client drivers are not supported.

The UNLOAD statement supports data lake Relational Engine tables. You can’t use the UNLOAD statement on proxy tables.



<a name="loio5049a399ee2241dda78d47a0a3cc46e9__section_esw_k1z_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loio5049a399ee2241dda78d47a0a3cc46e9__section_oxz_45w_brb"/>

## Examples

These examples unload data from data lake Files:

> ### Note:  
> To unload data to a non-default data lake Files container \(one outside of your data lake instance\), use <code>hdlfs://<i class="varname">&lt;container-name&gt;</i>/<i class="varname">&lt;filename&gt;</i></code> and include the CONNECTION\_STRING and WITH CREDENTIAL clauses.

-   This example unloads all data in table t1 to the default data lake Files container, in binary format:

    ```
    UNLOAD SELECT * FROM t1 
        INTO FILE 'hdlfs:///Q3_results.dat'
        FORMAT BINARY;
    ```

-   This example unloads all data in table foo in Parquet format using compression:

    ```
    UNLOAD SELECT * FROM foo 
        INTO FILE 'hdlfs:///unload_foo.parquet'
        FORMAT PARQUET
        COMPRESSION 'BROTLI';
    ```

-   This example unloads all data in table foo to a non-default data lake Files container \(one outside of your data lake instance\), using a connection string and credentials:

    ```
    UNLOAD SELECT * FROM foo 
        INTO FILE 'hdlfs://XXXXXXXX-XXXX-411c-821f-XXXXfd7f391c/unload_foo.csv'
        CONNECTION_STRING 'ENDPOINT=https://XXXXXXXX-XXXX-411c-821f-XXXXfd7f391c.files.hdl.XXXXXXX-XXX.XXXev-XXX.hanacloud.XXXXX.com'
        WITH CREDENTIAL 'MyCredential2';
    ```

-   This example unloads all data in table foo2 to the default data lake Files container, in Parquet format with a rowgroup size of 50 and a max file sixe of 500 KBs:

    ```
    UNLOAD SELECT * FROM foo2 
        INTO FILE 'hdlfs:///unload_foo2.parquet'
        FORMAT PARQUET
        ROW GROUP SIZE 2;
    ```


These examples unload the entire contents of table t1, using compression and parallel extraction:

-   This example unloads the entire contents of table t1 to Amazon S3, using compression and parallel extraction \(up to five threads\) with a part size of 10 MB:

    ```
    UNLOAD FROM TABLE t1 
        INTO FILE 's3://my_S3_data/Q3results^.gz'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
        	SECRET_ACCESS_KEY=abc;
        	REGION=eu-central-1;
        	SESSION_TOKEN=pqr'
        MAX PARALLEL DEGREE 5
        MAX PART SIZE 10 MB;
    ```

-   This example unloads the entire contents of table t1 to Azure storage, using compression and parallel extraction \(up to five threads\):

    ```
    UNLOAD FROM TABLE t1 
        INTO FILE 'bb://my_azure_data/Q3results^.gz'
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
        	AccountName=example;
        	AccountKey=example_key;
        	EndpointSuffix=core.windows.net'
        MAX PARALLEL DEGREE 5;
    ```

-   This example unloads the entire contents of table t1 to Google Cloud Storage, using compression and parallel extraction \(up to five threads\):

    ```
    UNLOAD FROM TABLE t1 
        INTO FILE 'gs://my_bucket/Q3results^.gz'
        CONNECTION_STRING 'client_email=XXXXXXXX;
        	PRIVATE_KEY=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
        	PRIVATE_KEY_ID=XXXXXXXX'
        MAX PARALLEL DEGREE 5;
    ```


**Related Information**  


[UNLOAD Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/7ad454a70dc84dbfbdfb2513e415fcd2.html "Exports data from data lake Relational Engine to either the external object store (Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, Google Cloud Storage) or to data lake Files containers (the managed object store).") :arrow_upper_right:

[SAP HANA Cloud, Data Lake Relational Engine Load and Unload Management](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/e77c96193a604e05ba198e424de2ed6c.html "Data load (import) and export (unload) procedures for data lake Relational Engine, including loading from and unloading to data lake Files.") :arrow_upper_right:

[Unloading Data to the External Object Store](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/31a19ffdd4af430c8ebc962cbac2cf5a.html "Unload (extract) data from data lake Relational Engine to the external object store using either the UNLOAD statement, or the data extraction facility.") :arrow_upper_right:

[Unloading Data to Data Lake Files from Data Lake Relational Engine](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2024_1_QRC/en-US/128c5bced169487f98eb2e2a49e7fd45.html "Use the UNLOAD statement to unload data to data lake Files.") :arrow_upper_right:

[TEMP_EXTRACT_GZ_COMPRESSION_LEVEL Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/ee9f6aaf17ec413dad8bd2c998adbf54.html "The compression level balances compression with speed when the TEMP_EXTRACT_COMPRESS option is set to ON.") :arrow_upper_right:

[SAP HANA Cloud, Data Lake Terminology](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2024_1_QRC/en-US/d003004765fb4475b14d83e5c51b117f.html "Definitions of data lake terms used in this document.") :arrow_upper_right:

