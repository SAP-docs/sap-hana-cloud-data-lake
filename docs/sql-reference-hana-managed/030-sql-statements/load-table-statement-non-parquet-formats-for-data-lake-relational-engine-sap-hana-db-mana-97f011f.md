<!-- loio97f011fc1d834d8ea920911caa9638f2 -->

# LOAD TABLE Statement \(Non-Parquet Formats\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Imports data into a data lake Relational Engine database table from either the external object store \(Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, or Google Cloud Storage\) or from data lake Files containers \(the managed object store\).



For information on loading data from Parquet files, see [LOAD TABLE Statement \(Parquet Format\) for Data Lake Relational Engine \(SAP HANA DB-Managed\)](load-table-statement-parquet-format-for-data-lake-relational-engine-sap-hana-db-managed-8af588a.md).



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure.



```
{ <owner> | <schema-name> }<schema-name>.]<table-name>
    [ <load-column> [, …] ]
     { <from-using-file>[, ...] | <wildcard-spec> [, ...] | <client-file>[, ...] }
    [ CONNECTION_STRING <connection-string> ]
    [ WITH CREDENTIAL <purpose-def> ]
    [ COMPRESSED | NOT COMPRESSED | AUTO COMPRESSED 
    DELIMITED BY ',';
    [ ENCODING '<encoding> '12345 ', c2, c3, FILLER(1))' ]
    [ BYTE ORDER MARK { ON | OFF } ]
    [ ENCRYPTED KEY '<key>' | NOT ENCRYPTED ]
    [ CHECK CONSTRAINTS { ON | OFF } ]
    [ DEFAULTS { ON | OFF } ]
    [ QUOTES { ON | OFF } ]
    [ QUOTE '<enclosure-character>' ]
    [ QUOTE ESCAPE '<escape-character>' ]
    ESCAPES OFF
    [ FORMAT { ASCII | BINARY | BCP | CSV } ]
    [ DELIMITED BY '<string>' ]
    [ STRIP { OFF | RTRIM } ]
    [ BYTE ORDER { NATIVE | LOW | HIGH } ]
    [ LIMIT <number-of-rows> ]
    [ NOTIFY <number-of-rows> ]
    [ ON FILE ERROR { ROLLBACK | FINISH | CONTINUE } ]
    [ PREVIEW { ON | OFF } ]
    [ ROW DELIMITED BY '<delimiter-string>' ' ]]
    [ SKIP <number-of-rows>] ]
    [ HEADER SKIP [ ALL ] <number> ]
    [ HEADER DELIMITED BY '<string>' ] 
    [ WORD SKIP <number> ]
    [ ON PARTIAL INPUT ROW { ROLLBACK | CONTINUE } ]
    [ IGNORE CONSTRAINT <constraint-type> <string> ]
    [ MESSAGE LOG '<string>' ]
    [ ROW LOG '<string>' ]
    [ ONLY LOG <log-what> [, …] ]
    [ LOG DELIMITED BY [, …] ]
    [ ALLOW MISSING COLUMNS { ON | OFF } ]
```

```
<load-column> ::=
   { LOAD [ INTO ] TABLE [ <column-name> [ <column-spec> ] [ <nulls-spec> ]   
   | FILLER ( [ <filler-type> ] ) 
   | <column-name> VALUE <default-value>}
```

```
<column-spec>LOAD [ INTO  ::=
   { ASCII ( <input-width> )
   | PREFIX { 1 | 2 | 4 }
   | BINARY [ <data-type> ] [ WITH NULL BYTE ]
   | { BINARY | ASCII } FILE ( <integer> )
   | { BINARY | ASCII } FILE ( '<string>' ) 
   | PREFIX { 1 | 2 | 4 } BINARY [ <data-type> ] [ WITH NULL BYTE ] [ VARYING ]
   | '<delimiter-string>'
   | DATE ( <input-date-format> )
   | DATETIME ( <input-datetime-format> )
   | FILE NAME
   | FILE ETAG
   | ENCRYPTED ( <data-type> '<key-string>' [, '<algorithm-string>' ] )
   | VALUE <default-value>
   | MISSING DEFAULT <default-value> }
   [ <nulls-spec> :: = NULL ( { BLANKS | ZEROS | '<literal>' } [, ...] ) ]
```

```
<filler-type> ::=
   { <input-width>
   | PREFIX { 1 | 2 | 4 }
   | '<delimiter-string>' }
```

```
<from-using-file> ::= { FROM | USING FILE } { '<filename-string>' | <filename-variable> } [WITH ETAG '<etag>']
```

```
<wildcard-spec> ::= <string containing at least one '*' character>
```

```
<client-file> ::= USING CLIENT FILE { '<filename-string>' | <filename-variable> }
```

```
<constraint-type> <string> ::=
   { CHECK <limit>
   | UNIQUE <limit>
   | NULL <limit>
   | FOREIGN KEY <limit> [, ...]
   | DATA VALUE <limit>
   | ALL <limit> }
```

```
<log-what> ::=
   { CHECK
   | ALL
   | NULL
   | UNIQUE
   | DATA VALUE
   | FOREIGN KEY
   | WORD }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio97f011fc1d834d8ea920911caa9638f2__section_mdz_zkr_brb"/>

## Parameters



### \{FROM | USING | USING CLIENT \} FILE


<dl>
<dt><b>



</b></dt>
<dd>

> ### Note:  
> The FROM and USING FILE clauses are synonymous.


<dl>
<dt><b>

Files Stored in Data Lake Files

</b></dt>
<dd>

The data source referenced by the filename is in a data lake Files container. The prefix `hdlfs:` identifies the file path as a data lake Files data source.

This example loads from a CSV file in the default data lake Files container:

```
LOAD TABLE t1(c1) FROM 'hdlfs:///employeelist.csv'
```

To connect to a non-default data lake Files container \(one outside of your data lake instance\), use this instead:

```
LOAD TABLE t1(c1) FROM 'hdlfs://<container-name>/<object-name>'
```



</dd><dt><b>

Files Stored in the External Object Store

</b></dt>
<dd>

In Azure Blob storage, *<filename-string\>* identifies the storage container name, and blob file name.

In Amazon S3, S3-compliant providers, and Google Cloud Storage, *<filename-string\>* identifies the bucket name, and object name.

> ### Note:  
> Container names, bucket names, and file names are case-sensitive in *<filename-string\>*.

```
<filename-string> ::= bb:// | pb:// | s3:// | gs:// 
```


<dl>
<dt><b>

bb://

</b></dt>
<dd>

Indicates "block blob". \(Azure only\)



</dd><dt><b>

pb://

</b></dt>
<dd>

Indicates "page blob". \(Azure only\)



</dd><dt><b>

s3://

</b></dt>
<dd>

Indicates "Amazon S3 bucketor S3-compliant buckets, such as SAP Converged Cloud"



</dd><dt><b>

gs://

</b></dt>
<dd>

Indicates Google Cloud Storage bucket. \(Google Cloud only\)



</dd>
</dl>

Since *<filename-string\>* is passed to the server as a string, it's subject to the same formatting requirements as other SQL strings. To specify more than one object, use a comma to separate each *<filename-string\>*.

If *<filename-string\>* WITH ETAG '<etag\>' is specified, the named object is loaded only if the ETag value matches. If a list of objects is specified and some of the ETags do not match, the LOAD statement will treat unmatched ETags as a file error and take the action specified by the ON FILE ERROR \{ ROLLBACK | FINISH | CONTINUE \} option. It will also be treated as a file error if the ETtag of an object changes while it is being loaded.

> ### Note:  
> Because of resource constraints, data lake Relational Engine doesn't guarantee that all the data can be loaded. If resource allocation fails, the entire load transaction is rolled back.

You can use *<wildcard-spec\>* to load a table from multiple files without needing to create a list of filenames. Use a single "\*" to match any character except a forward slash, "/'. For example, <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/file_*.dat</code> will match <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/file_1_3.dat</code> and <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/file_1.dat</code> but not <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/extra/file_2.dat</code>. Use the "\*\*" sequence to match every character including a forward slash, "/". For example, <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/parquet/**/*.parq</code> will match <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/parquet/c1=1/c2=2/file.parq</code> and <code>hdlfs://<i class="varname">&lt;endpoint&gt;</i>/path/to/parquet/c1=3/c2=2/file.parq</code>. If the *<wildcard-spec\>* doesn't match any filenames, no error is displayed.

Wildcard characters are supported for external object stores only. You can't specify wildcard characters in the first part of the prefix used to specify a container or bucket. For example, `hflfs://container*/path/to/file.csv` and `s3://bucket**/file.csv` are not valid. Only 10,000 files can be loaded after the *<wildcard-specs\>* have been expanded.



</dd><dt><b>

Files Stored on a Client

</b></dt>
<dd>

USING CLIENT FILE bulk loads one or more files from a client. Client-side bulk loading only supports single threaded processing for each file. When bulk loading external BLOBs \(using *<column-spec\>* FILE NAME\), the USING CLIENT FILE clause applies to both primary and secondary files.

Client-side bulk loading is supported by Interactive SQL and ODBC/JDBC clients using the Command Sequence protocol. It is not supported by clients using the TDS protocol. For data security over a network, use Transport Layer Security. To control who can use client-side bulk loads, use the secure feature \(-sf\) server startup switch, enable the ALLOW\_READ\_CLIENT\_FILE database option, and the READ CLIENT FILE access control.



</dd>
</dl>



</dd>
</dl>



### CONNECTION\_STRING *<connection-string\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies connection information.

```
<connection-string> ::= 
   { <non-default-hdlfs-instance> 
   | <azure-connection> 
   | <s3-connection>
   | <google-connection>}
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

This clause is optional for data lake Files containers. If you don't specify it, the LOAD statement will connect to the default data lake Files container provisioned within your data lake instance. If you do, the LOAD statement can connect to an alternate, non-default data lake Files container within a separate data lake instance.

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

*<azure-connection\>*

</b></dt>
<dd>

```
<azure-connection> ::= 'DEFAULTENDPOINTSPROTOCOL=<endpoint-protocol>;
	ACCOUNTNAME=<account-name>;
	ACCOUNTKEY=<account-key>;
	ENDPOINTSUFFIX=core.windows.net'
```

You can find *<azure-connection-string\>* in Azure portal. From your storage account, navigate to *Settings* \> *Access Keys*. Locate the *Connection string* section and copy the connection string to the clipboard. For *<azure-connection-string\>* examples, see the *Examples* section at the end of this topic.



</dd><dt><b>

*<s3-connection\>*

</b></dt>
<dd>

```
<s3-connection> ::= 'ENDPOINT=<endpoint>; 
	ENDPOINT_TYPE={PATH | VIRTUAL-HOST}; 
	ACCESS_KEY_ID=<access-key-string>; 
	SECRET_ACCESS_KEY=<secret-key string>; 
	REGION=<region-string>; 
	SESSION_TOKEN=<session-token>'
```

You can find your Amazon S3 option values in the AWS Management Console.

For Amazon S3 and any S3-compliant storage providers, such as SAP Converged Cloud, specify the following options for the *<connection-string\>* clause:


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

If you do not specify this option, the value defaults to server option iqdl\_aws\_region which defaults to us-east-1.



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

*<aws-connection\>*\(DEPRECATED\) The following syntax is deprecated as of QRC 2, 2022. Instead, use the syntax above for Amazon S3 and any S3-compliant storage providers.

</b></dt>
<dd>

```

 <aws-connection> ::=
	ACCESS_KEY_ID '<access-key-id>'
	SECRET_ACCESS_KEY '<secret-access-key>' 
	REGION '<AWS-region>'
```

You can find *<access-key-id\>*, *<secret-access-key\>*, and *<AWS-region\>* in the IAM console. For *<aws-connection\>* examples, see the *Examples* section at the end of this topic.



</dd><dt><b>

*<google-connection\>*

</b></dt>
<dd>

```
<google-connection> ::= 'CLIENT_EMAIL='<client-email>';
   PRIVATE_KEY='<private-key>';
   PRIVATE_KEY_ID='<private-key-id>'
```

You can find your *<google-connection\>* keys in Google Cloud Console, on the *Service Accounts* page. *<google-connection\>* accepts 'key=value' pairs separated by ';'. For *<google-connection\>* examples, see the *Examples* section at the end of this topic.



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



### COMPRESSED | NOT COMPRESSED | AUTO COMPRESSED


<dl>
<dt><b>



</b></dt>
<dd>

Specifies if the input files are compressed. If you're loading multiple input files in a single LOAD TABLE statement, this clause applies to all input files – you can't specify compression on a file-by-file basis.

If COMPRESSED is specified, data lake Relational Engine decompresses the data before loading it. If COMPRESSED is specified but the data is not compressed, then the load fails and returns an error.

If NOT COMPRESSED is specified, data lake Relational Engine loads the data without decompressing it.

The AUTO COMPRESSED clause is the default behavior, where data lake Relational Engine determines the compression property of each input file individually, based on its file extension `.gz` or `.gzip`.



</dd>
</dl>



### ENCODING '*<encoding\>*'


<dl>
<dt><b>



</b></dt>
<dd>

The ENCODING clause specifies the character set encoding of the input file. If the character set encoding is different from that of the database, character set conversion is performed during the load. If the data cannot be converted into the database character set, a conversion error is returned. If the ENCODING clause is not specified, the character set of the database is used. The clause applies to all files being loaded by the current LOAD TABLE statement. It's not possible to set different encoding options to individual files. The ENCODING clause does not work with binary load. An error occurs if either FORMAT BINARY is specified, or if a BINARY clause is specified in the column specification.

See [Character Set Encodings in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_4_QRC/en-US/8a8f277561e547b8a4a0fdfc7f7db7f7.html "A complete list of supported character set encodings for SAP HANA Cloud, data lake and their aliases.") :arrow_upper_right: for a complete list of supported character set encodings.



</dd>
</dl>



### BYTE ORDER MARK \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

By default data lake Relational Engine sets BYTE ORDER MARK to ON if the FORMAT is ASCII or BCP, and sets BYTE ORDER MARK to OFF if the FORMAT is BINARY, or if you specify BINARY in the column specification.



</dd>
<dd>

When BYTE ORDER MARK is set to ON, data lake Relational Engine searches for and interprets a byte order mark at the beginning of each input file. If a byte order mark is located, it's not considered to be part of the data to be loaded. If data lake Relational Engine cannot locate a byte order mark in the file, it assumes the byte order of that file to be NATIVE. When both the ENCODING and the BYTE ORDER clauses are specified, data lake Relational Engine checks that the byte order specified, or found, is consistent with the endianness of the encoding. An error occurs if the byte order is different from the endianness of the encoding.

If the ENCODING clause is specified:

-   If the BYTE ORDER MARK option is ON and you specify a UTF-16 encoding without an explicit endian, the database server searches for a BOM at the beginning of the data. If a BOM is present, it's used to determine the endianness of the data. Otherwise, the operating system endianness is assumed.

-   If the BYTE ORDER MARK option is ON and you specify a UTF-8 encoding, the server searches for a BOM at the beginning of the data. If a BOM is present, it's ignored.


If the ENCODING clause is not specified:

-   If you do not specify an ENCODING clause and the BYTE ORDER MARK option is ON, the server looks for a BOM at the beginning of the input data. If a BOM is located, the source encoding is automatically selected based on the encoding of the BOM \(UTF-16BE, UTF-16LE, or UTF-8\) and the BOM is not considered to be part of the data to be loaded.

-   If you do not specify an ENCODING clause and the BYTE ORDER MARK option is OFF, the database CHAR encoding is used, and the database server does not look for or interpret a BOM at the beginning of the data.


The BYTE ORDER clause does not work with binary load. An error occurs if either FORMAT BINARY is specified, or if a BINARY clause is specified in the column specification.



</dd>
</dl>



### ENCRYPTED KEY '*<key\>*' | NOT ENCRYPTED


<dl>
<dt><b>



</b></dt>
<dd>

\(Not to be confused with column-level encryption\) The ENCRYPTED clause specifies encryption settings for the input files. When loading encrypted data, you specify ENCRYPTED KEY followed by the key used to encrypt the data in the input file.

If the input file is both encrypted and compressed, the file is first decrypted and then decompressed.

If encryption is specified, the loading of each input file can only be done in single-threaded mode. However, different input files can be loaded concurrently, with one worker per file.



</dd>
<dd>

The clause applies to all files being loaded by the current LOAD TABLE statement. It's not possible to load from a combination of encrypted and non-encrypted files in the same statement.



</dd>
</dl>



### CHECK CONSTRAINTS \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

Evaluates check constraints, which you can ignore or log. CHECK CONSTRAINTS defaults to ON.

Setting CHECK CONSTRAINTS OFF causes data lake Relational Engine to ignore all check constraint violations. This can be useful, for example, during database rebuilding. If a table has check constraints that call user-defined functions that are not yet created, the rebuild fails unless this option is set to OFF.

This option is mutually exclusive to the following options. If any of these options are specified in the same load, an error results:

-   IGNORE CONSTRAINT ALL
-   IGNORE CONSTRAINT CHECK
-   LOG ALL
-   LOG CHECK



</dd>
</dl>



### DEFAULTS \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

Uses a column's default value. This option is ON by default. If the DEFAULTS option is OFF, any column not present in the column list is assigned NULL.

The setting for the DEFAULTS option applies to all column default values, including AUTOINCREMENT.



</dd>
</dl>



### QUOTES \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

Indicates that input strings are enclosed in quote characters. QUOTES is an optional clause and is ON by default. The first such character encountered in a string is treated as the quote character for the string. String data must be terminated with a matching quote.

With QUOTES ON, column or row delimiter characters can be included in the column value. Leading and ending quote characters are assumed not to be part of the value and are excluded from the loaded data value.

To include a quote character in a value with QUOTES ON, use two quotes. For example, this line includes a value in the third column that is a single quote character:

```
'123 High Street, Anytown', '(715)398-2354',''''
```

With STRIP turned on \(the default\), trailing blanks are stripped from values before they are inserted. Trailing blanks are stripped only for non-quoted strings. Quoted strings retain their trailing blanks. Leading blank or TAB characters are trimmed only when the setting is ON.

The data extraction facility provides options for handling quotes \(TEMP\_EXTRACT\_QUOTES, TEMP\_EXTRACT\_QUOTES\_ALL, and TEMP\_EXTRACT\_QUOTE\). If you plan to extract data to be loaded into an data lake Relational Engine main store table and the string fields contain column or row delimiter under default ASCII extraction, use the TEMP\_EXTRACT\_BINARY option for the extract and the FORMAT binary and QUOTES OFF clauses for LOAD TABLE.

Limits:

-   QUOTES ON applies only to column-delimited ASCII fields.
-   With QUOTES ON, the first character of a column delimiter or row terminator cannot be a single or double quote mark.
-   QUOTES ON forces single threaded processing for a given file.
-   The QUOTES option does not apply to loading binary large object \(BLOB\) or character large object \(CLOB\) data from the secondary file, regardless of its setting. A leading or trailing quote is loaded as part of CLOB data. Two consecutive quotes between enclosing quotes are loaded as two consecutive quotes with the QUOTES ON option.
-   SAP Adaptive Server Enterprise BCP does not support the QUOTES option. All field data is copied in or out equivalent to the QUOTES OFF setting. As QUOTES ON is the default setting for the data lake Relational Engine LOAD TABLE statement, specify QUOTES OFF when importing SAP ASE data from BCP output to a data lake Relational Engine table.

Exceptions:

-   If LOAD TABLE encounters any nonwhite characters after the ending quote character for an enclosed field, this error is reported and the load operation is rolled back:

    ```
    Non-SPACE text found after ending quote character for
    an enclosed field.
    SQLSTATE: QTA14    SQLCODE: -1005014L
    ```

-   With QUOTES ON, if a single or double quote is specified as the first character of the column delimiter, an error is reported and the load operation fails:

    ```
    Single or double quote mark cannot be the 1st character
    of column delimiter or row terminator with QUOTES option
    ON.
    SQLSTATE: QCA90    SQLCODE: -1013090L
    ```




</dd>
</dl>



### QUOTE *<enclosure-character\>*


<dl>
<dt><b>



</b></dt>
<dd>

For TEXT data only; identifies the enclosure character to be placed around string values. If not specified, the default QUOTE character is either a single \('\) or double \("\) quotation mark, depending on what is used in the field. If QUOTES OFF is defined, QUOTE is ignored.

If the specified *<enclosure-character\>* is multibyte, only the first byte is used; the remaining bytes are ignored.



</dd>
</dl>



### QUOTE ESCAPE '*<escape-character\>*'


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the escape character used in the data. If not specified, the default QUOTE ESCAPE character is the value of QUOTE. For example, if QUOTE is defined as percent \(%\), but QUOTE ESCAPE is not defined, the default value for QUOTE ESCAPE becomes %. If neither QUOTE ESCAPE nor QUOTE are defined, QUOTE defaults to either a single \('\) or double \("\) quotation mark, depending on what is used in the field, and QUOTE ESCAPE defaults to match QUOTE.

If the specified ESCAPE character is multibyte, only the first byte is used; the remaining bytes are ignored.

If QUOTES ON and QUOTE ESCAPE is not defined, single quote becomes the ESCAPE character and must be escaped by another quote.



</dd>
</dl>



### ESCAPES


<dl>
<dt><b>



</b></dt>
<dd>

For data lake Relational Engine, you need to set ESCAPES OFF.



</dd>
</dl>



### FORMAT \{ ASCII | BINARY | BCP | CSV \}


<dl>
<dt><b>



</b></dt>
<dd>


<dl>
<dt><b>

ASCII | BINARY

</b></dt>
<dd>

These formats are defined by *<column-spec\>*. If you omit that definition for a column, by default data lake Relational Engine uses the format defined by this option. Input lines are assumed to have ASCII \(the default\) or binary fields, one row per line, with values separated by the column delimiter character.



</dd><dt><b>

BCP

</b></dt>
<dd>

-   The BCP data file loaded into data lake Relational Engine tables must be exported \(BCP OUT\) in cross-platform file format using the -c option.
-   The default column delimiter for the LOAD TABLE statement is <tab\> and the default row terminator is <newline\>.
-   The last column in a row must be terminated by the row terminator, not by the column delimiter. If the column delimiter is present before the row terminator, then the column delimiter is treated as a part of the data.
-   Data for columns that are not the last column in the load specification must be delimited by the column delimiter only. If a row terminator is encountered before a column delimiter for a column that is not the last column, then the row terminator is treated as a part of the column data.
-   Column delimiter can be specified via the DELIMITED BY clause. For this format, the delimiter must be less than or equal to 10 characters in length. An error is returned, if the delimiter length is more than 10.
-   The load specification may contain only column names, NULL, and ENCRYPTED. An error is returned if any other option is specified in the load specification.

    For example, these LOAD TABLE load specifications are valid:

    ```
    LOAD TABLE x( c1, c2 null(blanks), c3 )
        FROM 'bcp_file.bcp'
        FORMAT BCP
        ...
    ```

    ```
    LOAD TABLE x( c1 encrypted(bigint,'KEY-ONE','aes'), c2, c3 )
        FROM 'bcp_file.bcp'
        FORMAT BCP
        ...
    ```




</dd>
</dl>


<dl>
<dt><b>

CSV

</b></dt>
<dd>

A row in a CSV file must be terminated either by a row deliminator \(default newline\) or a column deliminator \(default coma\) followed by a row delimiter. The maximum size of a delimiter is 4 bytes. An error message appears if the deliminator exceeds 4 bytes.

A CSV file may contain partial rows, defined as any row with the number of fields less than the number of columns specified \(either explicitly or implicitly\). All fields missing from a partial row are assigned a NULL value. If the column is not nullable, an error message appears, and no data is imported.

If a table has K columns, a CSV file has M fields, and the LOAD TABLE statement indicates N columns \(either explicitly or implicitly\), when N <= K and N < M, columns missing from the column list in the load statement are assigned default values.



</dd>
</dl>



</dd>
</dl>



### DELIMITED BY '*<string\>*'


<dl>
<dt><b>



</b></dt>
<dd>

If you omit a column delimiter in the *<column-spec\>* definition, the default column delimiter character is a comma. You can specify an alternative column delimiter by providing a single ASCII character or the hexadecimal character representation. The DELIMITED BY clause is:

```
... DELIMITED BY '\x09' ...
```

To use the newline character as a delimiter, you can specify either the special combination '\\n' or its ASCII value '\\x0a'. Although you can specify up to four characters in the *<column-spec\>* *<delimiter-string\>*, you can specify only a single character in the DELIMITED BY clause.

When specifying the DATE column with the NULL clause, the date column is treated as a variable-width date field if DELIMITED BY clause is included. Otherwise, date column is treated as fixed-width date field.



</dd>
</dl>



### STRIP \{ OFF | RTRIM \}


<dl>
<dt><b>



</b></dt>
<dd>

Determines whether unquoted values should have trailing blanks stripped off before they are inserted. These STRIP keywords are accepted:

-   STRIP OFF – does not strip off trailing blanks
-   STRIP RTRIM – strips trailing blanks.
-   STRIP ON – is deprecated. Use STRIP RTRIM.

With STRIP turned on \(the default\), data lake Relational Engine strips trailing blanks from values before inserting them. This is effective only for VARCHAR data. STRIP OFF preserves trailing blanks.

Trailing blanks are stripped only for unquoted strings. Quoted strings retain their trailing blanks. If you do not require blank sensitivity, you can use the FILLER option as an alternative to be more specific in the number of bytes to strip, instead of all the trailing spaces. STRIP OFF is more efficient for data lake Relational Engine, and it adheres to the ANSI standard when dealing with trailing blanks. \(CHAR data is always padded, so the STRIP option only affects VARCHAR data.\)

The STRIP option applies only to variable-length non-binary data and does not apply to ASCII fixed-width inserts. For example, assume this schema:

```
CREATE TABLE t( c1 VARCHAR(3) );
LOAD TABLE t( c1 ',' ) ........ STRIP RTRIM    // trailing blanks trimmed

LOAD TABLE t( c1 ',' ) ........ STRIP OFF      // trailing blanks not trimmed

LOAD TABLE t( c1 ASCII(3) ) ... STRIP RTRIM    // trailing blanks not trimmed
LOAD TABLE t( c1 ASCII(3) ) ... STRIP OFF      // trailing blanks trimmed

LOAD TABLE t( c1 BINARY ) ..... STRIP RTRIM    // trailing blanks trimmed
LOAD TABLE t( c1 BINARY ) ..... STRIP OFF      // trailing blanks trimmed
```

Trailing blanks are always trimmed from binary data.



</dd>
</dl>



### BYTE ORDER \{ NATIVE | LOW | HIGH \}


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the byte order during reads. This option applies to all binary input fields. You cannot set different BYTE ORDER options for individual files. If no BYTE ORDER is defined, the default is NATIVE. You can specify:

-   NATIVE – \(default\) data lake Relational Engine always reads binary data in the format native to the machine it is running on.
-   HIGH – when multibyte quantities have the high-order byte first \(for big-endian platforms\).
-   LOW – when multibyte quantities have the low-order byte first \(for little-endian platforms\).



</dd>
</dl>



### LIMIT *<number-of-rows\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the maximum number of rows to insert into the table. The default is 0 for no limit. The maximum is 2<sup>31</sup> - 1 \(2147483647\) rows.

Any LIMIT clause only applies to the load, not to each file. Multiple objects are processed in parallel, except when using the LIMIT clause. If a LIMIT clause is specified, the entire load process is single threaded, and the number of rows are loaded from the objects in the order specified in the LOAD TABLE statement.



</dd>
</dl>



### NOTIFY *<number-of-rows\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies that you be notified with a message each time the specified number of rows is successfully inserted into the table. The default is 0, meaning no notifications are printed. The value of this option overrides the value of the NOTIFY\_MODULUS database option.



</dd>
</dl>



### ON FILE ERROR \{ ROLLBACK | FINISH | CONTINUE \}


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the action data lake Relational Engine takes when an input file cannot be opened because it does not exist or you have incorrect privileges to read the file. You can specify one of the following:

-   ROLLBACK – returns an error and aborts the entire transaction \(the default\).
-   FINISH – finishes the insertions already completed and ends the load operation.
-   CONTINUE – skips the file to continue the load operation.

Only one ON FILE ERROR clause is permitted.



</dd>
</dl>



### PREVIEW \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

Sends messages to the client application describing the layout of input into the destination table including starting position, name, and data type of each column. Data lake Relational Engine sends this information at the start of the load process. If you are writing to a log file, this information is also included in the log.



</dd>
</dl>



### ROW DELIMITED BY '*<delimiter-string\>*'


<dl>
<dt><b>



</b></dt>
<dd>

Specifies a string up to 4 bytes in length that indicates the end of an input record. You can use this option only if all fields within the row are any of the following:

-   Delimited with column terminators
-   Data defined by the DATE or DATETIME *<column-spec\>* options
-   ASCII fixed-length fields

Always include ROW DELIMITED BY to ensure parallel loads. Omitting this clause from the LOAD specification may cause data lake Relational Engine to load serially rather than in parallel.

You cannot use this clause if any input fields contain binary data. With this clause, a row terminator causes any missing fields to be set to NULL. All rows must have the same row delimiters, and it must be distinct from all column delimiters. The row and field delimiter strings cannot be an initial subset of each other. For example, you cannot specify "\*" as a field delimiter and "\*\#" as the row delimiter, but you could specify "\#" as the field delimiter with that row delimiter.

If a row is missing its delimiters, data lake Relational Engine returns an error and rolls back the entire load transaction. The only exception is the final record of a file where it rolls back that row and returns a warning message.



</dd>
</dl>



### SKIP *<number-of-rows\>*


<dl>
<dt><b>



</b></dt>
<dd>

Defines the number of rows to skip at the beginning of the input tables for this load. The maximum number of rows to skip is 2<sup>31</sup> - 1 \(2147483647\). SKIP runs in single-threaded mode as it reads the rows to skip. Any SKIP clause only applies to the load not to each file.

The default is 0.



</dd>
</dl>



### HEADER SKIP \[ALL\] *<number\>* … HEADER DELIMITED BY '*<string\>*'


<dl>
<dt><b>



</b></dt>
<dd>

When you include ALL in your load statement for a multiple-file load, LOAD TABLE skips the number of header rows \(that you specify with *<number\>*\) from the start of each file, while omitting ALL just skips the number of header rows from just the first file. ALL does not change the results for a single-file load.

HEADER SKIP *<number\>*, without ALL, specifies a number of lines at the beginning of the data file, including header rows, for LOAD TABLE to skip. All LOAD TABLE column specifications and other load options are ignored, until the specified number of rows is skipped.

-   The number of lines to skip is greater than or equal to zero.
-   Lines are determined by a 1-to-4-character delimiter string specified in the HEADER DELIMITED BY clause. The default HEADER DELIMITED BY string is the \\n character.
-   The HEADER DELIMITED BY string has a maximum length of four characters. An error is returned, if the string length is greater than four or less than one.
-   When a non-zero HEADER SKIP value is specified, all data inclusive of the HEADER DELIMITED BY delimiter is ignored, until the delimiter is encountered the number of times specified in the HEADER SKIP clause.
-   All LOAD TABLE column specifications and other load options are ignored, until the specified number of rows has been skipped. After the specified number of rows has been skipped, the LOAD TABLE column specifications and other load options are applied to the remaining data.
-   The "header" bytes are ignored only at the beginning of the data. When multiple files are specified in the USING clause, HEADER SKIP only ignores data starting from the first row of the first file, until it skips the specified number of header rows, even if those rows exist in subsequent files. LOAD TABLE does not look for headers once it starts parsing actual data.
-   No error is reported if LOAD TABLE processes all input data before skipping the number of rows specified by HEADER SKIP.

HEADER SKIP ALL has the following behaviors:

-   You cannot specify HEADER SKIP and HEADER SKIP ALL in the same LOAD TABLE statement; doing so results in an error.
-   You can specify HEADER SKIP ALL *<number\>* and SKIP *<number-of-rows\>* together. When you do, the number of header rows \(specified in *<number\>*\) is skipped first, then SKIP *<number-of-rows\>* is performed until the statement reaches the number of rows you specified.
-   You can specify HEADER SKIP ALL *<number\>* and LIMIT *<number-of-rows\>*. When you do, the number of header rows \(specified in *<number\>*\) is skipped first, then rows are loaded for the number of rows you specify.



</dd>
</dl>



### WORD SKIP *<number\>*


<dl>
<dt><b>



</b></dt>
<dd>

Allows the load to continue when it encounters data longer than the limit specified when the word index was created.

If a row is not loaded because a word exceeds the maximum permitted size, a warning is written to the `.iqmsg` file. WORD size violations can be optionally logged to the MESSAGE LOG file and rejected rows logged to the ROW LOG file specified in the LOAD TABLE statement.

-   If the option is not specified, LOAD TABLE reports an error and rolls back on the first occurrence of a word that is longer than the specified limit.
-   *<number\>* specifies the number of times the “***Words exceeding the maximum permitted word length not supported***” error is ignored.
-   0 \(zero\) means there is no limit.



</dd>
</dl>



### ON PARTIAL INPUT ROW \{ ROLLBACK | CONTINUE \}


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the action to take when a partial input row is encountered during a load. You can specify one of the following:

-   CONTINUE – \(default\) issues a warning and continues the load operation.
-   ROLLBACK – aborts the entire load operation and reports the error:

    ```
    Partial input record skipped at EOF.
    SQLSTATE: QDC32    SQLSTATE: -1000232L
    ```




</dd>
</dl>



### IGNORE CONSTRAINT *<constraint-type\>* *<string\>*


<dl>
<dt><b>



</b></dt>
<dd>

Specifies whether to ignore CHECK, UNIQUE, NULL, DATA VALUE, and FOREIGN KEY integrity constraint violations that occur during a load. *<string\>* is an integer that indicates the maximum number of violations to ignore before initiating a rollback. Specifying each *<constraint-type\>* has the following result:

-   CHECK *<limit\>* – if *<limit\>* specifies zero, the number of CHECK constraint violations to ignore is infinite. If CHECK is not specified, the first occurrence of any CHECK constraint violation causes the LOAD TABLE statement to roll back. If *<limit\>* is nonzero, then the *<limit\>* +1 occurrence of a CHECK constraint violation causes the load to roll back.
-   UNIQUE *<limit\>* – if *<limit\>* specifies zero, then the number of UNIQUE constraint violations to ignore is infinite. If *<limit\>* is nonzero, then the *<limit\>* +1 occurrence of a UNIQUE constraint violation causes the load to roll back.
-   NULL *<limit\>* – if *<limit\>* specifies zero, then the number of NULL constraint violations to ignore is infinite. If *<limit\>* is nonzero, then the *<limit\>* +1 occurrence of a NULL constraint violation causes the load to roll back.
-   FOREIGN KEY *<limit\>* – if *<limit\>* specifies zero, the number of FOREIGN KEY constraint violations to ignore is infinite. If *<limit\>* is nonzero, then the *<limit\>* +1 occurrence of a FOREIGN KEY constraint violation causes the load to roll back.
-   DATA VALUE *<limit\>* – if the database option CONVERSION\_ERROR = ON, an error is reported and the statement rolls back. If *<limit\>* specifies zero, then the number of DATA VALUE constraint violations \(data type conversion errors\) to ignore is infinite. If *<limit\>* is nonzero, then the *<limit\>* +1 occurrence of a DATA VALUE constraint violation causes the load to roll back.
-   ALL *<limit\>* – if the CONVERSION\_ERROR database option is ON, an error is reported and the statement rolls back. If *<limit\>* specifies zero, then the cumulative total of all integrity constraint violations to ignore is infinite. If *<limit\>* is nonzero, then load rolls back when the cumulative total of all ignored UNIQUE, NULL, DATA VALUE, and FOREIGN KEY integrity constraint violations exceeds the value of *<limit\>*. For example, if you specify this IGNORE CONSTRAINT option, the total number of integrity constraint violations cannot exceed 200, whereas the total number of NULL and UNIQUE constraint violations cannot exceed 50 and 100, respectively:

    ```
    IGNORE CONSTRAINT NULL 50, UNIQUE 100, ALL 200
    ```

    Whenever any of these limits is exceeded, the LOAD TABLE statement rolls back.

    > ### Note:  
    > A single row can have more than one integrity constraint violation. Every occurrence of an integrity constraint violation counts towards the limit of that type of violation.
    > 
    > Set the IGNORE CONSTRAINT option limit to a nonzero value if you are logging the ignored integrity constraint violations. Logging an excessive number of violations affects the performance of the load


If CHECK, UNIQUE, NULL, or FOREIGN KEY is not specified in the IGNORE CONSTRAINT clause, then the load rolls back on the first occurrence of each of these types of integrity constraint violation.

If DATA VALUE is not specified in the IGNORE CONSTRAINT clause, then the load rolls back on the first occurrence of this type of integrity constraint violation, unless the CONVERSION\_ERROR database option is OFF. If so, a warning is reported for any DATA VALUE constraint violation and the load continues.

When the load completes, an informational message regarding integrity constraint violations is logged in the `.iqmsg` file. This message contains the number of integrity constraint violations that occurred during the load and the number of rows that were skipped.



</dd>
</dl>



### MESSAGE LOG '*<string\>*' ROW LOG '*<string\>*'


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the names of files in which to log information about integrity constraint violations and the types of violations to log. Timestamps indicating the start and completion of the load are logged in both the MESSAGE LOG and the ROW LOG files. Both MESSAGE LOG and ROW LOG must be specified, or no information about integrity violations is logged.

-   If the ONLY LOG clause is not specified, no information on integrity constraint violations is logged. Only the timestamps indicating the start and completion of the load are logged.
-   Information is logged on all integrity constraint-type violations specified in the ONLY LOG clause or for all word index-length violations if the keyword WORD is specified.
-   If constraint violations are being logged, every occurrence of an integrity constraint violation generates exactly one row of information in the MESSAGE LOG file.

    The number of rows \(errors reported\) in the MESSAGE LOG file can exceed the IGNORE CONSTRAINT option limit, because the load is performed by multiple threads running in parallel. More than one thread might report that the number of constraint violations has exceeded the specified limit.

-   If constraint violations are being logged, exactly one row of information is logged in the ROW LOG file for a given row, regardless of the number of integrity constraint violations that occur on that row.

    The number of distinct errors in the MESSAGE LOG file might not exactly match the number of rows in the ROW LOG file. The difference in the number of rows is due to the parallel processing of the load described above for the MESSAGE LOG.

-   If the MESSAGE LOG or ROW LOG file already exists, the file is overwritten.
-   Specifying an invalid file name for the MESSAGE LOG or ROW LOG file generates an error.
-   Specifying the same file name for the MESSAGE LOG and ROW LOG files generates an error.

Various combinations of the IGNORE CONSTRAINT and MESSAGE LOG clauses result in different logging actions:


<table>
<tr>
<th valign="top">

IGNORE CONSTRAINT Specified?

</th>
<th valign="top">

MESSAGE LOG Specified?

</th>
<th valign="top">

Action

</th>
</tr>
<tr>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

All ignored integrity constraint violations are logged, including the user specified limit, before the rollback.

</td>
</tr>
<tr>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

The first integrity constraint violation is logged before the rollback.

</td>
</tr>
<tr>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Nothing is logged.

</td>
</tr>
<tr>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

Nothing is logged. The first integrity constraint violation causes a rollback.

</td>
</tr>
</table>

> ### Tip:  
> Set the IGNORE CONSTRAINT clause limit to a nonzero value, if you are logging the ignored integrity constraint violations. If a single row has more than one integrity constraint violation, a row for each violation is written to the MESSAGE LOG file. Logging an excessive number of violations affects the performance of the load.



</dd>
</dl>



### LOG DELIMITED BY


<dl>
<dt><b>



</b></dt>
<dd>

Specifies the separator between data values in the ROW LOG file. The default separator is a comma.



</dd>
</dl>



### ALLOW MISSING COLUMNS \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

Determines the behavior when one or more columns in the LOAD TABLE statement cannot be matched with a column in a given file. The default value is OFF. When this clause is OFF, the statement fails if a column cannot be matched.

When this clause is ON, columns that cannot be matched are populated with the column's default value. If no default value is defined, NULL values are loaded. If the column has no default value and is defined as NOT NULL, the statement fails.

Use the MISSING DEFAULT column option to specify a default value to use when the column cannot be matched.



</dd>
</dl>



<a name="loio97f011fc1d834d8ea920911caa9638f2__section_qdr_blr_brb"/>

## Remarks

The LOAD TABLE statement allows efficient mass insertion into a database table from multiple file types. Its clauses also let you control load behavior when integrity constraints are violated and to log information about the violations.

The LOAD TABLE statement can load compressed objects only in gzip format. Any object with an extension `.gz` or `.gzip` is compressed. Secondary files aren't supported during a compressed load. Compressed and uncompressed objects can be specified in the same LOAD TABLE statement. Each compressed object in a load is processed by one thread.

You can use LOAD TABLE on a temporary table, but the temporary table must have been declared with ON COMMIT PRESERVE ROWS or the next COMMIT removes the rows you've loaded.

LOAD TABLE supports loading of large object \(LOB\) data.



### Error Messages

-   If the specified load format isn't ASCII, BINARY, BCP, or CSV data lake Relational Engine returns the message “***Only ASCII, BCP, BINARY, PARQUET, and CSV are supported LOAD formats.***”
-   For FORMAT BCP, if the LOAD TABLE column specification contains anything other than column name, NULL, or ENCRYPTED, data lake Relational Engine returns the error message “***Invalid load specification for LOAD ... FORMAT BCP.***”
-   If the column delimiter or row terminator size for FORMAT BCP is greater than 10 characters, data lake Relational Engine returns the message “***Delimiter '%2' must be 1 to %3 characters in length.***” \(where %3 equals 10\).

    Messages corresponding to error or warning conditions, which can occur for FORMAT BCP as well as FORMAT ASCII, are the same for both formats.

-   If the load default value specified is AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT, data lake Relational Engine returns the error “***Default value %2 cannot be used as a LOAD default value. %1***”
-   If the LOAD TABLE specification doesn't contain any columns that need to be loaded from the file specified, data lake Relational Engine returns the error “***The LOAD statement must contain at least one column to be loaded from input file.***” and the LOAD TABLE statement rolls back.
-   If a load exceeds the limit on the maximum number of terms for a text document with TEXT indexes, data lake Relational Engine returns the error “***Text document exceeds maximum number of terms. Support up to 4294967295 terms per document.***”



### Column Options

For ASCII, BINARY, CSV and BCP formats, data lake Relational Engine supports both character and binary data and it support both fixed- and variable-length formats. To handle all of these formats, supply a *<load-column\>* to tell data lake Relational Engine what kind of data to expect from each “column” or field in the source file. The *<column-spec\>* lets you define these formats:

-   ASCII with a fixed length of bytes. The *<input-width\>* value is an integer indicating the fixed width in bytes of the input field in every record.
-   Binary or nonbinary fields that use a PREFIX clause are comprised of two parts:


    <table>
    <tr>
    <th valign="top">

    Part
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Prefix portion
    
    </td>
    <td valign="top">
    
    Always a binary value.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Associated data portion
    
    </td>
    <td valign="top">
    
    If you use:

    -   The PREFIX clause without BINARY – a character format \(ASCII data\)
    -   The PREFIX clause with BINARY – a binary format and which can only be specified for a VARCHAR or VARBINARY column.


    
    </td>
    </tr>
    </table>
    
    When you perform a load of binary data, the length of the associated data portion differs based on whether you specify the VARYING option with the PREFIX clause:

    -   PREFIX *<n\>* BINARY with VARYING – the length of the associated data portion is variable, and is the same as the actual data length.

    -   PREFIX *<n\>* BINARY without VARYING – the length of the associated data portion is fixed, and is the declared length for the varchar/varbinary column. For example, if the column is varchar\(10\), the associated data portion is 10 bytes long. The prefix portion indicates the actual length of data in the field, even if that length isn't shorter than the field in the file — in which case, the remaining data after the actual data is ignored, and is inserted in the column in the table.


    Specifying FORMAT BINARY PREFIX\(*<n\>* \) VARYING on the UNLOAD statement allows you to extract the varchar or varbinary column without trailing padding in the extracted file. With FORMAT BINARY PREFIX\( *<n\>* \), trailing blanks for the varchar column \(and trailing zeros for the varbinary column\) aren't stripped from values when inserted into the column.

    If you unload data using FORMAT BINARY, use the BINARY WITH NULL BYTE clause for each column when you load the binary data.

    When loading binary data, you can specify the data type of the input file. Defining the data type can help you avoid conversion errors if an unexpected data type change occurs for the column. If you don't specify *<data-type\>* in the BINARY WITH NULL BYTE parameter, data lake assumes the input field has the same data type as the column.

-   Variable-length characters delimited by a separator. You can specify the terminator as hexadecimal ASCII characters and the bytes \(1, 2, or 4\) to specify the length of the input. This *<delimiter-string\>* variable-length characters, delimited by a separator, can be any string of up to 4 characters, including any combination of printable characters, and any 8-bit hexadecimal ASCII code that represents a nonprinting character. For example, specify:

    -   "\\x09" to represent a tab as the terminator.
    -   "\\x00" for a null terminator \(no visible terminator as in “C” strings\).
    -   "\\x0a" for a newline character as the terminator. You can also use the special character combination of '\\n' for newline.

    > ### Note:  
    > The delimiter string can be from 1 to 4 characters long, but you can specify only a single character in the DELIMITED BY clause. For BCP, the delimiter can be up to 10 characters.

-   DATE or DATETIME string as ASCII characters. Define the *<input-date-format\>* or *<input-datetime-format\>* of the string using one of the corresponding formats for the date and datetime data types supported by data lake Relational Engine. Use DATE for DATE values and DATETIME for DATETIME and TIME values. Formatting dates and times are:


    <table>
    <tr>
    <th valign="top" rowspan="1">

    Option
    
    </th>
    <th valign="top" rowspan="1">

    Meaning
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    yyyy or YYYY

    yy or YY
    
    </td>
    <td valign="top">
    
    Represents the number of the year. Default is the current year.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    mm or MM
    
    </td>
    <td valign="top">
    
    Represents the number of the month. Always use leading zero or blank for the number of the month where appropriate. For example, '05' for May. DATE value must include a month. For example, if the DATE value you enter is 1998, you receive an error. If you enter '03', data lake Relational Engine applies the default year and day and converts it to '1998-03-01'.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    dd or DD

    jjj or JJJ
    
    </td>
    <td valign="top">
    
    Represents the number of the day. Default day is 01. Always use leading zeros for number of day where appropriate, for example, '01' for first day. J or j indicates a Julian day \(1 to 366\) of the year.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    hh or HH
    
    </td>
    <td valign="top">
    
    Represents the hour. Hour is based on a 24-hour clock. Always use leading zeros or blanks for hour where appropriate, for example, '01' for 1 am. '00' is also valid value for hour of 12 a.m.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    nn
    
    </td>
    <td valign="top">
    
    Represents the minute. Always use leading zeros for minute where appropriate, for example, '08' for 8 minutes.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    ss\[.ssssss\]
    
    </td>
    <td valign="top">
    
    Represents seconds and fraction of a second.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    aa
    
    </td>
    <td valign="top">
    
    Represents the a.m. or p.m. designation.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    pp
    
    </td>
    <td valign="top">
    
    Represents the p.m. designation, only if needed.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    hh
    
    </td>
    <td valign="top">
    
    Data lake Relational Engine assumes zero for minutes and seconds. For example, if the data lake Relational Engine value you enter is '03', data lake Relational Engine converts it to '03:00:00.0000'.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    hh:nn or hh:mm
    
    </td>
    <td valign="top">
    
    Data lake Relational Engine assumes zero for seconds. For example, if the time value you enter is '03:25', data lake Relational Engine converts it to '03:25:00.0000'.
    
    </td>
    </tr>
    </table>
    
    Sample DATE and DATETIME format options are:


    <table>
    <tr>
    <th valign="top" rowspan="1">

    Input data
    
    </th>
    <th valign="top" rowspan="1">

    Format specification
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    12/31/98
    
    </td>
    <td valign="top">
    
    DATE \('MM/DD/YY'\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    19981231
    
    </td>
    <td valign="top">
    
    DATE \('YYYYMMDD'\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    123198140150
    
    </td>
    <td valign="top">
    
    DATETIME \('MMDDYYhhnnss'\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    14:01:50 12-31-98
    
    </td>
    <td valign="top">
    
    DATETIME \('hh:nn:ss MM-DD-YY'\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    18:27:53
    
    </td>
    <td valign="top">
    
    DATETIME \('hh:nn:ss'\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    12/31/98 02:01:50AM
    
    </td>
    <td valign="top">
    
    DATETIME \('MM/DD/YY hh:nn:ssaa'\)
    
    </td>
    </tr>
    </table>
    
-   The FILE NAME option allows you to insert the name of the originating file into a FILE NAME column when you perform a LOAD INTO TABLE statement. When you do, the name of the originating file \(but not its contents\) is loaded into the FILE NAME column for each of the rows in the table.

    -   You can only specify this option for VARCHAR and CHAR columns.
    -   The length of the file name can't be longer than the maximum length of the column you're specifying.
    -   You can only specify one column for use with FILE NAME.
    -   After the load inserts the file name into a column, the system doesn't add any information to mark the column as a FILE NAME column.
    -   The column you specify for FILE NAME can't contain any data.

-   The FILE ETAG option allows you to insert the ETag of the originating file into a FILE ETAG column when you perform a LOAD INTO TABLE statement. When you do, the ETag of the originating file is loaded into the FILE ETAG column for each of the rows in the table.

    -   You can only specify this option for VARCHAR and CHAR columns.
    -   The length of the ETag can't be longer than the maximum length of the column you're specifying.
    -   You can only specify one column for use with FILE ETAG.
    -   After the load inserts the file name into a column, the system doesn't add any information to mark the column as a FILE ETAG column.
    -   The column you specify for FILE ETAG can't contain any data.


Data lake Relational Engine has built-in load optimizations for common date, time, and datetime formats. If your data to be loaded matches one of these formats, you can significantly decrease load time by using the appropriate format.

You can also specify the date/time field as an ASCII fixed-width field \(as described above\) and use the FILLER\(1\) option to skip the column delimiter.

The NULL portion of the *<column-spec\>* indicates how to treat certain input values as NULL values when loading into the table column. These characters can include BLANKS, ZEROS, or any other list of literals you define. When specifying a NULL value or reading a NULL value from the source file, the destination column must be able to contain NULLs.

ZEROS are interpreted as follows: the cell is set to NULL if \(and only if\) the input data \(before conversion, if ASCII\) is all binary zeros \(and not character zeros\).

-   If the input data is character zero, then:

    1.  NULL \(ZEROS\) never causes the cell to be NULL.
    2.  NULL \('0'\) causes the cell to be NULL.

-   If the input data is binary zero \(all bits clear\), then:

    1.  NULL \(ZEROS\) causes the cell to be NULL.
    2.  NULL \('0'\) never causes the cell to be NULL.


For example, if your LOAD TABLE statement includes col1 date\('yymmdd'\) null\(zeros\) and the date is 000000, you receive an error indicating that 000000 can't be converted to a DATE\(4\). To get LOAD TABLE to insert a NULL value in col1 when the data isn't 000000, either write the NULL clause as null\('000000'\), or modify the data to equal binary zeros and use NULL \(ZEROS\).

If the length of a VARCHAR cell is zero and the cell is NULL, you get a zero-length cell. For all other data types, if the length of the cell is zero, data lake Relational Engine inserts a NULL. This is ANSI behavior. For non-ANSI treatment of zero-length character data, set the NON\_ANSI\_NULL\_VARCHAR database option.

Use the VALUE clause to specify a load default column value. You can load a default value into a column, even if the column doesn't have a default value defined in the table schema. This feature provides more flexibility at load time.

-   The LOAD TABLE DEFAULTS option must be ON in order to use the default value specified in the LOAD TABLE statement. If the DEFAULTS option is OFF, the specified load default value is used and a NULL value is inserted into the column instead.
-   The LOAD TABLE statement must contain at least one column that needs to be loaded from the file specified in the LOAD TABLE statement. Otherwise, an error is reported and the load is performed.
-   The specified load default value must conform to the supported default values for columns and default value restrictions. The LOAD TABLE DEFAULT option doesn't support AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT as a load default value.
-   Encryption of the default value isn't supported for the load default values specified in the VALUE clause.
-   A constraint violation caused by evaluation of the specified load default value is counted for each row that is inserted in the table.

Use the MISSING DEFAULT option to specify a default column value to use if the column cannot be matched with a column in the loaded file. This option only applies when ALLOW MISSING COLUMNS is ON.

Another important part of the *<load-column\>* is the FILLER option. This option indicates you want to skip over a specified field in the source input file. For example, there may be characters at the end of rows or even entire fields in the input files that you don't want to add to the table. As with the *<column-spec\>* definition, FILLER specifies ASCII fixed length of bytes, variable length characters delimited by a separator, and binary fields using PREFIX bytes.



<a name="loio97f011fc1d834d8ea920911caa9638f2__section_h1v_jdy_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using the SAP HANA database REMOTE\_EXECUTE procedure:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loio97f011fc1d834d8ea920911caa9638f2__section_h4x_hlr_brb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio97f011fc1d834d8ea920911caa9638f2__section_n41_jlr_brb"/>

## Examples

**Example 1:** This example loads 14 columns into table T1 from the object `MULTI.DAT`.

-   Example 1 syntax for Azure:

    ```
    LOAD TABLE T1
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 'bb://MY_AZURE_CONTAINER_1/MULTI.DAT'
        ROW DELIMITED BY '\x0a'
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
            AccountName=example;
            AccountKey=example_key;
            EndpointSuffix=core.windows.net'
        ESCAPES OFF;
    ```

-   Example 1 syntax for Amazon S3:

    ```
    LOAD TABLE T1
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 's3://MY_BUCKET_1/MULTI.DAT'
        ROW DELIMITED BY '\x0a'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        ESCAPES OFF;
    ```

-   Example 1 syntax for Google Cloud:

    ```
    LOAD TABLE T1
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 'gs://my_bucket/object.dat'
        ROW DELIMITED BY '\x0a'
        CONNECTION_STRING 'client_email=XXXXXXXX;
            private_key=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
            private_key_id=XXXXXXXX'
        ESCAPES OFF;
    ```


**Example 2:** This example loads the compressed object COMPRESSED.GZ. The server checks the file extension of the object name. If the extension is .GZ, it uses gzip compression \(other compression types cause an error\).

-   Example 2 syntax for Azure:

    ```
    LOAD TABLE T2
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 'bb://MY_AZURE_CONTAINER_2/COMPRESSED.GZ'
        ROW DELIMITED BY '\x0a'
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
            AccountName=example;AccountKey=example_key;
            EndpointSuffix=core.windows.net'
        ESCAPES OFF;
    ```

-   Example 2 syntax for Amazon S3:

    ```
    LOAD TABLE T2
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 's3://MY_BUCKET_2/COMPRESSED.GZ'
        ROW DELIMITED BY '\x0a'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        ESCAPES OFF;
    ```

-   Example 2 syntax for Google Cloud:

    ```
    LOAD TABLE T2
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 'gs://MY_BUCKET_2/COMPRESSED.GZ'
        ROW DELIMITED BY '\x0a'
        CONNECTION_STRING 'client_email=XXXXXXXX;
            private_key=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
            private_key_id=XXXXXXXX'
            ESCAPES OFF;
    ```


**Example 3:**This example loads a list of objects from cloud storage. The list can be a mixture of compressed and uncompressed objects. The server loads these objects in parallel. Your data uses the pipe \( | \) delimiter rather than the default comma \( , \) delimiter.

-   Example 3 syntax for Azure:

    ```
    LOAD TABLE T3
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 'bb://MY_AZURE_CONTAINER_3/PART_1_1.DAT','bb://MY_AZURE_CONTAINER_3/PART_2_1.DAT','bb://MY_AZURE_CONTAINER_3/PART_3_1.DAT'
        DELIMITED BY '|'
        ROW DELIMITED BY '\x0a'	
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
            AccountName=example;
            AccountKey=example_key;
            EndpointSuffix=core.windows.net'
            ESCAPES OFF;
    ```

-   Example 3 syntax for Amazon S3:

    ```
    LOAD TABLE T3
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 's3://MY_BUCKET_3/PART_1_1.DAT','s3://MY_BUCKET_3/PART_2_1.DAT','s3://MY_BUCKET_3/PART_3_1.DAT'
        DELIMITED BY '|'
        ROW DELIMITED BY '\x0a'	
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
            ESCAPES OFF;
    ```

-   Example 3 syntax for Google Cloud:

    ```
    LOAD TABLE T3
        ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
        USING FILE 'gs://MY_BUCKET_3/PART_1_1.DAT','gs://MY_BUCKET_3/PART_2_1.DAT','gs://MY_BUCKET_3/PART_3_1.DAT'
        DELIMITED BY '|'
        ROW DELIMITED BY '\x0a'	
        CONNECTION_STRING 'client_email=XXXXXXXX;
            private_key=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
            private_key_id=XXXXXXXX'
            ESCAPES OFF;
    ```


**Example 4:** This example loads 5 columns of binary data into table T4 from the object `MULTI.DAT`. Each data field in the input file was terminated with x01, which instructs the load to insert NULL into the column. Note that the ROW DELIMITED BY clause isn't permitted with binary data. The FORMAT BINARY clause is required.

-   Example 4 syntax for Azure:

    ```
    LOAD TABLE T4 
        ( C1 BINARY WITH NULL BYTE, C2 BINARY WITH NULL BYTE, C3 BINARY WITH NULL BYTE, C4 BINARY WITH NULL BYTE, C5 BINARY WITH NULL BYTE )
        USING FILE 'bb://MY_AZURE_CONTAINER_4/MULTI.DAT'
        FORMAT BINARY
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
            AccountName=example;
            AccountKey=example_key;
            EndpointSuffix=core.windows.net'
        ESCAPES OFF;
    ```

-   Example 4 syntax for Amazon S3:

    ```
    LOAD TABLE T4 
        ( C1 BINARY WITH NULL BYTE, C2 BINARY WITH NULL BYTE, C3 BINARY WITH NULL BYTE, C4 BINARY WITH NULL BYTE, C5 BINARY WITH NULL BYTE )
        USING FILE 's3://MY_BUCKET_4/MULTI.DAT'
        FORMAT BINARY
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
            ESCAPES OFF;
    ```

-   Example 4 syntax for Google Cloud:

    ```
    LOAD TABLE T4 
        ( C1 BINARY WITH NULL BYTE, C2 BINARY WITH NULL BYTE, C3 BINARY WITH NULL BYTE, C4 BINARY WITH NULL BYTE, C5 BINARY WITH NULL BYTE )
        USING FILE 'gs://MY_BUCKET_4/MULTI.DAT'
        FORMAT BINARY
        CONNECTION_STRING 'client_email=XXXXXXXX;
            private_key=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
            private_key_id=XXXXXXXX'
            ESCAPES OFF;
    ```


**Example 5:**This example loads BLOBs and CLOBs. The primary file `MY_TEST_.INP` contains four secondary files:

-   `TEST.HTML`

-   `FP-NUMERIC.INP.GZ`

-   `ABC_DATA.INP`

-   `DEF_DATA.INP.GZ`


Assume the credentials supplied to the LOAD TABLE statement enable read access to the primary file, as well as all the secondary files. The ASCII FILE keyword specifies that the column value is the name of an object that is loaded as a CLOB, and the BINARY FILE keyword specifies the named object is loaded as a BLOB.

-   Example 5 syntax for Azure:

    ```
    LOAD TABLE T5 
        (C1,C2,C3 ASCII FILE (',') NULL('NULL'),C4 BINARY FILE (',') NULL('NULL'))
        FROM 'bb://MY_AZURE_CONTAINER_5/DATA/MY_TEST_.IMP'
        ROW DELIMITED BY '\X0A'
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
            AccountName=example;
            AccountKey=example_key;
            EndpointSuffix=core.windows.net'
        QUOTES OFF 
        ESCAPES OFF;
    ```

-   Example 5 syntax for Amazon S3:

    ```
    LOAD TABLE T5 
        (C1,C2,C3 ASCII FILE (',') NULL('NULL'),C4 BINARY FILE (',') NULL('NULL'))
        FROM 's3://MY_BUCKET_5/DATA/MY_TEST_.IMP'
        ROW DELIMITED BY '\X0A'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        QUOTES OFF 
        ESCAPES OFF;
    ```

-   Example 5 syntax for Google Cloud:

    ```
    LOAD TABLE T5 (C1,C2,C3 ASCII FILE (',') NULL('NULL'),C4 BINARY FILE (',') NULL('NULL'))
        FROM 'gs://MY_BUCKET_5/DATA/MY_TEST_.IMP'
        ROW DELIMITED BY '\X0A'
        CONNECTION_STRING 'client_email=XXXXXXXX;
            private_key=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
            private_key_id=XXXXXXXX'
        QUOTES OFF 
        ESCAPES OFF;
    ```


**Example 6:** These examples load data from data lake Files:

-   This example loads data from a csv file on a defaultdata lake Files container:

    > ### Note:  
    > To load data from a non-default data lake Files container \(one outside of your data lake instance\), use <code>hdlfs://<i class="varname">&lt;container-name&gt;</i>/<i class="varname">&lt;filename&gt;</i></code> and include the CONNECTION\_STRING and WITH CREDENTIAL clauses.

    ```
    LOAD TABLE T7 (c1) 
        FROM 'hdlfs:///employeelist.csv'
        FORMAT CSV
        ESCAPES OFF;  
    ```

-   This examples loads data from a non-default data lake Files container using the CONNECTION\_STRING and WITH CREDENTIAL clauses.

    ```
    LOAD TABLE region (r_regionkey, r_name, r_comment ) 
        FROM 'hdlfs://XXXXXXXX-XXXX-411c-821f-XXXXfd7f391c/myregion.csv'
        CONNECTION_STRING 'ENDPOINT=https://XXXXXXXX-XXXX-411c-821f-XXXXfd7f391c.files.hdl.XXXXXXX-XXX.XXXev-XXX.hanacloud.XXXXX.com'
        FORMAT CSV
        ROW DELIMITED BY '\n' 
        QUOTES OFF
        ESCAPES OFF
        WITH CREDENTIAL 'MyCredential2';
    ```


**Additional Examples:**

-   This example loads data from a file `abcd.inp` on a client machine:

    ```
    LOAD TABLE t1(c1,c2,FILLER(30))
        USING CLIENT FILE 'abcd.inp'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        QUOTES OFF 
        ESCAPES OFF
        IGNORE CONSTRAINT UNIQUE 0, NULL 0
        MESSAGE LOG 's3://MY_BUCKET_6/m.log'
        ROW LOG 's3://MY_BUCKET_6/r.log' ONLY LOG UNIQUE
    ```

-   This example loads data from two files into the product\_new table \(which allows NULL values\). The tab character is the default column delimiter, and the newline character is the row delimiter:

    ```
    LOAD TABLE product_new
        ( id,
        name,
        description,
        size,
        color   '\x09'   NULL( 'null', 'none', 'na' ),
        quantity   PREFIX 2,
        unit_price   PREFIX 2 )
        FROM 'bb://MY_AZURE_CONTAINER_1/MULTI.DAT', 'bb://MY_AZURE_CONTAINER_1/MULTI2.DAT',
        CONNECTION_STRING 'DefaultEndpointsProtocol=https;
            AccountName=example;
            AccountKey=example_key;
            EndpointSuffix=core.windows.net',
        QUOTES OFF ESCAPES OFF
        FORMAT ascii
        DELIMITED BY '\x09'
        ON FILE ERROR CONTINUE
        ROW DELIMITED BY '\n'
    ```

-   This example ignores 10 word-length violations; on the 11th, it deploys the new error and rolls back the load:

    ```
    load table PTAB1(
           ck1         ','  null ('NULL') ,
           ck3fk2c2    ','  null ('NULL') ,
           ck4         ','  null ('NULL') ,
           ck5         ','  null ('NULL') ,
           ck6c1       ','  null ('NULL') ,
           ck6c2       ','  null ('NULL') ,
           rid         ','  null ('NULL')  )
    FROM 's3://MY_BUCKET_6/ri_index_selfRI.inp'
    	  CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
               SECRET_ACCESS_KEY=abc;
               REGION=eu-central-1;
               SESSION_TOKEN=pqr'
           row delimited by '\n'
           LIMIT 14   SKIP 10
           IGNORE CONSTRAINT UNIQUE 2, FOREIGN KEY 8
           word skip 10 quotes off escapes off strip
           off
    ...
    ```

-   This example loads data into table t1 from the BCP character file `bcp_file.bcp` using the FORMAT BCP load option:

    ```
    LOAD TABLE t1 (c1, c2, c3)
        FROM 's3://MY_BUCKET_6/bcp_file.bcp'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
        REGION=eu-central-1;
        SESSION_TOKEN=pqr'
        FORMAT BCP
    ...
    ```

-   This example loads default values 12345 into c1 using the VALUE load option, and load c2 and c3 with data from the `LoadConst04.dat` file:

    ```
    LOAD TABLE t1 (c1 VALUE '12345 ', c2, c3, FILLER(1))
        FROM 's3://MY_BUCKET_6/LoadConst04.dat'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        STRIP OFF
        QUOTES OFF ESCAPES OFF
        DELIMITED BY ',';
    ```

-   This example loads c1 and c2 with data from the file `bcp_file.bcp` using the FORMAT BCP load option and set c3 to the value 10:

    ```
    LOAD TABLE t1 (c1, c2, c3 VALUE '10')
        FROM LOAD TABLE t1(c1,c2,FILLER(30))
        USING CLIENT FILE 's3://MY_BUCKET_6/bcp_file.bcp'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        FORMAT BCP
        QUOTES OFF 
        ESCAPES OFF;
    ```

-   This code fragment ignores one header row at the beginning of the data file, where the header row is delimited by '&&':

    ```
    LOAD TABLE
    ...HEADER SKIP 1 HEADER DELIMITED by '&&'
    ...
    ```

-   This code fragment ignores 2 header rows at the beginning of the data file, where each header row is delimited by '\\n':

    ```
    LOAD TABLE
    ...HEADER SKIP 2
    ...
    ```

-   This example loads a table from a CSV file, using a double quotation mark for the QUOTE enclosure character and the backslash \(\\\) for the QUOTE ESCAPE character.

    ```
    LOAD TABLE tab1(c1, c2, c3)
        FROM 's3://MY_BUCKET_6/foo.csv'
        CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
            SECRET_ACCESS_KEY=abc;
            REGION=eu-central-1;
            SESSION_TOKEN=pqr'
        DELIMITED BY ','
        ROW DELIMITED BY '\n'
        QUOTES ON ESCAPES OFF
        QUOTE '"'
        QUOTE ESCAPE '\'
        FORMAT CSV;
    ```

    If QUOTE ESCAPE isn't specified and foo.csv file contains:

    -   """',"\\\\","\\abc"
    -   "\\a\\b\\c","\\\\\\\\","""\\dog"""

    Executing the following LOAD TABLE statement:

    ```
    LOAD TABLE tab1(c1,c2,c3) 
            FROM 's3://MY_BUCKET_6/foo.csv'
            CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
                SECRET_ACCESS_KEY=abc;
                REGION=eu-central-1;
                SESSION_TOKEN=pqr'
            DELIMITED BY ','
            ROW DELIMITED BY '\n' 
            QUOTES ON ESCAPES OFF
            QUOTE '"'
            FORMAT CSV;
    ```

    Loads the data as:

    -   c1 c2 c3
    -   " \\\\ \\abc
    -   \\a\\b\\c \\\\\\\\ "dog"

-   This example loads a table, inserting the names of the files \(`DATAFILE1.CSV` and `DATAFILE2.CSV`\) into the c2 column as specified by FILE NAME:

    ```
    LOAD INTO TABLE test2 (c1, c2 FILE NAME, c3)
            USING FILE 's3://MY_BUCKET/DATAFILE1.CSV', 'S3://MY_BUCKET/DATAFILE2.CSV'
    	   CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
                SECRET_ACCESS_KEY=abc;
                REGION=eu-central-1;
                SESSION_TOKEN=pqr'
            QUOTES OFF 
            ESCAPES OFF 
            FORMAT CSV
            DELIMITED BY ',' 
            ROW DELIMITED BY '\n' ;
    ```

    In this example, the content of `datefile1.csv` is:

    ```
    c1_val1, c3_value1,
    c1_val2, c3_value2,
    ```

    The content of `datefile2.csv` is:

    ```
    c1_val21, c3_value21,
    c1_val22, c3_value22,
    ```

    After the load, the test2 table contains the following:

    ```
    
    c1                c2                    c3
    =========         ========              =========
    c1_val1           datefile1.csv         c3_value1
    c1_val2           datefile1.csv         c3_value2
    c1_val21          datefile2.csv         c3_value21
    c1_val22          datefile2.csv         c3_value22
    ```

-   This example loads a table named test2 \(which contains columns c1 and c2, both of which are VARCHAR\(20\)\), using files `datafile1.csv` and `datafile2.csv`, skipping the first header row from the start of each file:

    ```
    LOAD INTO TABLE test2 (c1, c2 )
            USING FILE 's3://MY_BUCKET/DATAFILE1.CSV', 'S3://MY_BUCKET/DATAFILE2.CSV',
    	   CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
                SECRET_ACCESS_KEY=abc;
                REGION=eu-central-1;
                SESSION_TOKEN=pqr'	   
            QUOTES OFF 
            ESCAPES OFF 
            FORMAT CSV
            HEADER SKIP ALL 1 DELIMITED BY ',' ROW DELIMITED BY '\n' ;
    ```

    In this example, the content of `datefile1.csv` is:

    ```
    c1_val1, c3_value1,
    c1_val2, c3_value2,
    ```

    The content of `datefile2.csv` is:

    ```
    c1_val1, c3_value1,
    c1_val2, c3_value2,
    ```

    After the load, the contents of the test2 table are:

    ```
    c1                c2       
    =========         ======
    c1_val2         c3_value2
    c1_val22        c3_value22
    ```

-   To execute a VARCHAR or VARBINARY load from a file unloaded using FORMAT BINARY, use the BINARY WITH NULL BYTE clause for each column :

    ```
    LOAD TABLE t1 (c1 BINARY WITH NULL BYTE) FROM 'yyy' FORMAT BINARY
    ```

    You can specify this LOAD *<column-spec\>*, binary, for any column data type — the column in this example is c1.

-   This example uses the prefix *<n\>* binary option to specify a VARCHAR or VARBINARY load from a file unloaded using the FORMAT BINARY PREFIX\( *<n\>* \) clause set to 2, where c1 is a VARCHAR column:

    ```
    LOAD TABLE t1 (c1 PREFIX 2 BINARY WITH NULL BYTE) FROM 'xxx' FORMAT BINARY
    ```

    You can only specify prefix *<n\>* binary for VARCHAR and VARBINARY columns; which in this example is c1.


**Related Information**  


[LOAD TABLE Statement (Non-Parquet Formats) for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/7ca3f60902f3473296cb309533d89210.html "Imports data into a data lake Relational Engine database table from either the external object store (Azure BLOB storage, an Amazon S3 bucket, an S3-compliant bucket, or Google Cloud Storage) or from data lake Files containers (the managed object store).") :arrow_upper_right:

[SAP HANA Cloud, Data Lake Relational Engine Load and Unload Management](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/e77c96193a604e05ba198e424de2ed6c.html "Data load (import) and export (unload) procedures for data lake Relational Engine, including loading from and unloading to data lake Files.") :arrow_upper_right:

[Loading Data from Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/e52d8274e0364e868fd02ec3c2b3ed9c.html "Use the data lake Relational Engine LOAD TABLE statement to load data into a data lake Relational Engine table from Azure Blob storage.") :arrow_upper_right:

[Loading Data from the Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/9e9a558cf14a44bc812e2562afcd116f.html "Use the LOAD TABLE statement to load data into a data lake Relational Engine table from your Amazon S3 bucket.") :arrow_upper_right:

[Loading Data from Google Cloud Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/a723d42f6c3d4d5ab9f2a1424130d10c.html "Use the LOAD TABLE statement to load data into a data lake Relational Engine table from your Google Cloud Storage bucket.") :arrow_upper_right:

[Loading Data From Data Lake Files to Data Lake Relational Engine](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/ac82036515a749bea5a55a64b43031a4.html "Specify the location in your LOAD TABLE statement to load data into data lake Relational Engine from data lake Files.") :arrow_upper_right:

[Loading Parquet Files](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_4_QRC/en-US/a054ac0ce09e47799e5f24860378056b.html "Parquet is an efficient, open-source, column-oriented format file designed for Apache Hadoop. You can load tables in Parquet format using the data lake Relational Engine LOAD TABLE statement.") :arrow_upper_right:

[TEMP\_EXTRACT\_MAX\_PARALLEL\_DEGREE Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/temp-extract-max-parallel-degree-option-for-data-lake-relational-engine-sap-hana-db-manag-8b1135e.md "Sets the maximum parallel degree for the data extraction facility. The TEMP_EXTRACT_MAX_PARALLEL_DEGREE option limits the maximum number of threads that run in parallel to extract data.")

[TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/temp-extract-varying-option-for-data-lake-relational-engine-sap-hana-db-managed-a975dc5.md "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.")

[SAP HANA Cloud, Data Lake Terminology](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_4_QRC/en-US/d003004765fb4475b14d83e5c51b117f.html "Definitions of data lake terms used in this document.") :arrow_upper_right:

