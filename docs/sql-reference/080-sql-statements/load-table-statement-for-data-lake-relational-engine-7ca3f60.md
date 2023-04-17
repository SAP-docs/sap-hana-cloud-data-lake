<!-- loio7ca3f60902f3473296cb309533d89210 -->

# LOAD TABLE Statement for Data Lake Relational Engine

Imports data into a data lake Relational Engine database table from either the external object store \(Azure BLOB storage, an Amazon S3 bucket, S3-compliant bucket, or a Google Cloud Storage\) or from data lake Files containers \(the managed object store\).



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
LOAD [ INTO ] TABLE [ { [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <schema-name> (varname] }.]<table-name>
    ( <load-specification> [, …] )
     { <from-using-file>[, ...] | <client-file>[, ...] | <parquet-load-group>[, ...] }
    [ CONNECTION_STRING <connection-string> ]
    [ COMPRESSED | NOT COMPRESSED | AUTO COMPRESSED ]
    [ ENCODING '<encoding>' ]
    [ BYTE ORDER MARK { ON | OFF } ]
    [ ENCRYPTED KEY '<key>' | NOT ENCRYPTED ]
    [ CHECK CONSTRAINTS { ON | OFF } ]
    [ DEFAULTS { ON | OFF } ]
    [ QUOTES { ON | OFF } ]
    [ QUOTE '<enclosure-character>' ]
    [ QUOTE ESCAPE '<escape-character>' ]
    ESCAPES OFF
    [ FORMAT { ascii | binary | bcp | csv | parquet } ]
    [ DELIMITED BY '<string>' ]
    [ STRIP { OFF | RTRIM } ]
    [ BYTE ORDER { NATIVE | LOW | HIGH } ]
    [ LIMIT <number-of-rows> ]
    [ NOTIFY <number-of-rows> ]
    [ ON FILE ERROR { ROLLBACK | FINISH | CONTINUE } ]
    [ PREVIEW { ON | OFF } ]
    [ ROW DELIMITED BY '<delimiter-string>' ]
    [ SKIP <number-of-rows> ]
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
    [ WITH MATCHING COLUMN NAMES ]
```

```
<load-specification> ::=
   { <column-name> [ [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <parquet-from-column> (varname] ] [ <filler-type> <column-spec> ] 
   | <column-name> { { BINARY | ASCII } FILE( <integer> ) | { BINARY | ASCII } FILE ( '<string>' ) }   
   | FILLER ( <filler-type> ) }
```

```
<parquet-from-column> ::=
   FROM COLUMN { '<parquet-column-name>' | <parquet-column-position> }
```

```
<column-spec> ::=
   { ASCII ( <input-width> )
   | PREFIX { 1 | 2 | 4 }
   | BINARY [ <data-type> ] [ WITH NULL BYTE ] 
   | PREFIX { 1 | 2 | 4 } BINARY [ <data-type> ] [ WITH NULL BYTE ] [ VARYING ]
   | '<delimiter-string>'
   | DATE ( <input-date-format> )
   | DATETIME ( <input-datetime-format> )
   | FILE NAME
   | FILE ETAG
   | ENCRYPTED ( <data-type> '<key-string>' [, '<algorithm-string>' ] )
   | VALUE <default-value>
   | MISSING DEFAULT [/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <default-value> (varname] }
   [ NULL ( { BLANKS | ZEROS | '<literal>' } [, ...] ) ]
```

```
<filler-type> ::=
   { <input-width>
   | PREFIX { 1 | 2 | 4 }
   | '<delimiter-string>' }
```

```
<from-using-file> ::= { FROM | USING FILE } { '<filename-string>' | <filename-variable> } [WITH ETAG '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <etag> (varname]']
```

```
<client-file> ::= USING CLIENT FILE { '<filename-string>' | <filename-variable> }
```

```
<parquet-load-group> ::=
   ( <load-specification> [, …] )
   FROM { '<filename-string>' | <filename-variable> } [WITH ETAG '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <etag> (varname]'] 
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
> Testing with a dataset modeled from a real-world use-case, we achieved upload speeds of 14.8 GB/min and 117.3 million rows/min.



<a name="loio7ca3f60902f3473296cb309533d89210__load_table_parameters1"/>

## Parameters

 \{FROM | USING \[ CLIENT \] FILE\}
 :   > ### Note:  
> The FROM and USING FILE clauses are synonymous.

     Files Stored in data lake Files
     :   The data source referenced by the filename is in the default data lake Files container.

        The prefix `hdlfs:` identifies the file path as a data lake Files data source.

        This example loads from a CSV file:

        ```
        LOAD TABLE t1(c1) FROM 'hdlfs:///employeelist.csv'
        ```

      Files Stored in the External Object Store
     :   In Azure Blob storage, *<filename-string\>* identifies the storage container name, and blob file name.

        In Amazon S3, S3-compliant provders, and Google Cloud Storage, *<filename-string\>* identifies the bucket name, and object name.

        > ### Note:  
        > Container names, bucket names, and file names are case-sensitive in *<filename-string\>*.

        ```
        <filename-string> ::= bb:// | pb:// | s3:// | gs:// 
        ```

         bb://
         :   Indicates "block blob". \(Azure only\)

          pb://
         :   Indicates "page blob". \(Azure only\)

          s3://
         :   Indicates "Amazon S3 bucketor S3-compliant buckets, such as SAP Converged Cloud"

          gs://
         :   Indicates Google Cloud Storage bucket. \(Google Cloud only\)

         Since *<filename-string\>* is passed to the server as a string, it's subject to the same formatting requirements as other SQL strings.

        To specify more than one object, use a comma to separate each *<filename-string\>*.

        If *<filename-string\>* WITH ETAG '<etag\>' is specified, the named object is loaded only if the ETag value matches. If a list of objects is specified and some of the ETags do not match, the LOAD statement will treat unmatched ETags as a file error and take the action specified by the ON FILE ERROR \{ ROLLBACK | FINISH | CONTINUE \} option. It will also be treated as a file error if the ETtag of an object changes while it is being loaded.

        Because of resource constraints, data lake Relational Engine doesn't guarantee that all the data can be loaded. If resource allocation fails, the entire load transaction is rolled back. Any SKIP or LIMIT clause only applies in the beginning of the load, not to each file. Multiple objects are processed in parallel, except when using the SKIP or LIMIT clauses. The rows being skipped are processed single threaded from the objects in the order specified in the LOAD statement. Once the SKIP completes, the rest of the objects are processed in parallel if there's no LIMIT clause. If a LIMIT clause is specified, the entire load process is single threaded, and the number of rows are loaded from the objects in the order specified in the LOAD TABLE statement.

        The LOAD TABLE statement can load compressed objects only in gzip format. Any object with an extension `.gz` or `.gzip` is compressed. Secondary files aren't supported during a compressed load. Compressed and uncompressed objects can be specified in the same LOAD TABLE statement. Each compressed object in a load is processed by one thread.

        USING CLIENT FILE bulk loads one or more files from a client. The character set of the file on the client side must be the same as the server collation. Client-side bulk loading incurs no administrative overhead, such as extra storage space, memory, or network-monitoring daemon requirements, but does forces single threaded processing for each file.

        When bulk loading large objects, the USING CLIENT FILE clause applies to both primary and secondary files.

        Client-side bulk loading is supported by Interactive SQL and ODBC/JDBC clients using the Command Sequence protocol. It is not supported by clients using the TDS protocol. For data security over a network, use Transport Layer Security. To control who can use client-side bulk loads, use the secure feature \(-sf\) server startup switch, enable the ALLOW\_READ\_CLIENT\_FILE database option, and the READ CLIENT FILE access control.

   CONNECTION\_STRING *<connection-string\>* 
 :   Specifies connection information

    ```
    <connection-string> ::= 
       { <azure-connection> 
       | <s3-connection>  
       | <google-connection>}
    ```

     *<azure-connection\>*
     :   ```
<azure-connection> ::= 'DEFAULTENDPOINTSPROTOCOL=<endpoint-protocol>;
	ACCOUNTNAME=<account-name>;
	ACCOUNTKEY=<account-key>;
	ENDPOINTSUFFIX=core.windows.net'
```

        You can find *<azure-connection-string\>* in Azure portal. From your storage account, navigate to *Settings* \> *Access Keys*. Locate the *Connection string* section and copy the connection string to the clipboard. For *<azure-connection-string\>* examples, see the *Examples* section at the end of this topic.

      *<s3-connection\>*
     :   ```
<s3-connection> ::= 'ENDPOINT=<endpoint>; 
	ENDPOINT_TYPE={PATH | VIRTUAL-HOST}; 
	ACCESS_KEY_ID=<access-key-string>; 
	SECRET_ACCESS_KEY=<secret-key string>; 
	REGION=<region-string>; 
	SESSION_TOKEN=<session-token>'
```

        You can find your Amazon S3 option values in the AWS Management Console.

        For Amazon S3 and any S3-compliant storage providers, such as SAP Converged Cloud, specify the following options for the *<connection-string\>* clause:

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

         :   If you do not specify this option, the value defaults to server option iqdl\_aws\_region which defaults to us-east-1.

         :   If both this and the ENDPOINT option are specified, the value for REGION needs to be consistent with the value for ENDPOINT.

         :   If specified, but no value is provided, you are connected to a backend that uses a single server with no concept of regions.

          SESSION\_TOKEN
         :   If specified, the Amazon S3 client SDK will use its value when creating Amazon S3 credentials. If not specified it will be treated as an absence of MFA access for the account.

       *<aws-connection\>*
     \(DEPRECATED\) The following syntax is deprecated as of QRC 2, 2022. Instead, use the syntax above for Amazon S3 and any S3-compliant storage providers.
     :   ```

 <aws-connection> ::=
	ACCESS_KEY_ID '<access-key-id>'
	SECRET_ACCESS_KEY '<secret-access-key>' 
	REGION '<AWS-region>'
```

        You can find *<access-key-id\>*, *<secret-access-key\>*, and *<AWS-region\>* in the IAM console. For *<aws-connection\>* examples, see the *Examples* section at the end of this topic.

      *<google-connection\>*
     :   ```
<google-connection> ::= 'CLIENT_EMAIL='<client-email>';
   PRIVATE_KEY='<private-key>';
   PRIVATE_KEY_ID='<private-key-id>'
```

        You can find your *<google-connection\>* keys in Google Cloud Console, on the *Service Accounts* page. *<google-connection\>* accepts 'key=value' pairs separated by ';'. For *<google-connection\>* examples, see the *Examples* section at the end of this topic.

   COMPRESSED | NOT COMPRESSED | AUTO COMPRESSED
 :   Specifies if the input files are compressed. If you're loading multiple input files in a single LOAD TABLE statement, this clause applies to all input files – you can't specify compression on a file-by-file basis.

    If COMPRESSED is specified, data lake Relational Engine decompresses the data before loading it. If COMPRESSED is specified but the data is not compressed, then the load fails and returns an error.

    If NOT COMPRESSED is specified, data lake Relational Engine loads the data without decompressing it.

    The AUTO COMPRESSED clause is the default behavior, where data lake Relational Engine determines the compression property of each input file individually, based on its file extension `.gz` or `.gzip`.

  ENCODING '*<encoding\>*'
 :   The ENCODING clause specifies the character set encoding of the input file. If the character set encoding is different from that of the database, character set conversion is performed during the load. If the data cannot be converted into the database character set, a conversion error is returned. If the ENCODING clause is not specified, the character set of the database is used. The clause applies to all files being loaded by the current LOAD TABLE statement. It's not possible to set different encoding options to individual files.The ENCODING clause does not work with binary load. An error occurs if either FORMAT BINARY is specified, or if a BINARY clause is specified in the column specification.

    See [Character Set Encodings in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_1_QRC/en-US/8a8f277561e547b8a4a0fdfc7f7db7f7.html "A complete list of supported character set encodings for SAP HANA Cloud, data lake and their aliases.") :arrow_upper_right: for a complete list of supported character set encodings.

  BYTE ORDER MARK \{ ON | OFF \}
 :   By default data lake Relational Engine sets BYTE ORDER MARK to ON if the FORMAT is ASCII or BCP, and sets BYTE ORDER MARK to OFF if the FORMAT is BINARY, or if you specify BINARY in the column specification.

 :   When BYTE ORDER MARK is set to ON, data lake Relational Engine searches for and interprets a byte order mark at the beginning of each input file. If a byte order mark is located, it's not considered to be part of the data to be loaded. If data lake Relational Engine cannot locate a byte order mark in the file, it assumes the byte order of that file to be NATIVE. When both the ENCODING and the BYTE ORDER clauses are specified, data lake Relational Engine checks that the byte order specified, or found, is consistent with the endianness of the encoding. An error occurs if the byte order is different from the endianness of the encoding. Data lake Relational Engine decrypts the data in the input files using the provided encryption key and algorithm. If the ENCRYPTED clause is not specified or if NOT ENCRYPTED is specified, it checks that the byte order specified, or found, is consistent with the endianness of the encoding. An error occurs if the byte order is different from the endianness of the encoding.

    If the ENCODING clause is specified:

    -   If the BYTE ORDER MARK option is ON and you specify a UTF-16 encoding without an explicit endian, the database server searches for a BOM at the beginning of the data. If a BOM is present, it's used to determine the endianness of the data. Otherwise, the operating system endianness is assumed.

    -   If the BYTE ORDER MARK option is ON and you specify a UTF-8 encoding, the server searches for a BOM at the beginning of the data. If a BOM is present, it's ignored.


    If the ENCODING clause is not specified:

    -   If you do not specify an ENCODING clause and the BYTE ORDER MARK option is ON, the server looks for a BOM at the beginning of the input data. If a BOM is located, the source encoding is automatically selected based on the encoding of the BOM \(UTF-16BE, UTF-16LE, or UTF-8\) and the BOM is not considered to be part of the data to be loaded.

    -   If you do not specify an ENCODING clause and the BYTE ORDER MARK option is OFF, the database CHAR encoding is used, and the database server does not look for or interpret a BOM at the beginning of the data.


    The BYTE ORDER clause does not work with binary load. An error occurs if either FORMAT BINARY is specified, or if a BINARY clause is specified in the column specification.

  ENCRYPTED KEY '*<key\>*' | NOT ENCRYPTED
 :   \(Not to be confused with column-level encryption\) The ENCRYPTED clause specifies encryption settings for the input files. When loading encrypted data, you specify ENCRYPTED KEY followed by the key used to encrypt the data in the input file.

    If ENCRYPTED is specified, data lake Relational Engine checks that the byte order specified, or found, is consistent with the endianness of the encoding. An error occurs if the byte order is different from the endianness of the encoding. Data lake Relational Engine decrypts the data in the input files using the provided encryption key and algorithm. If the ENCRYPTED clause is not specified or if NOT ENCRYPTED is specified, it checks that the byte order specified, or found, is consistent with the endianness of the encoding. An error occurs if the byte order is different from the endianness of the encoding and data lake Relational Engine will not decrypt the data.

    It is possible to specify NOT ENCRYPTED even if the input file is actually encrypted. In this case, the data is loaded without decryption, and remains encrypted in the database.

    If the input file is both encrypted and compressed, the file is first decrypted and then decompressed.

    If the BYTE ORDER MARK option is ON and you specify a UTF-16

    If the input file is both encrypted and compressed, the load will not work if NOT ENCRYPTED and COMPRESSED are specified. This is because decompression requires the data to be decrypted first.

    If encryption is specified, the loading of each input file can only be done in single-threaded mode. However, different input files can be loaded concurrently, with one worker per file.

 :   The clause applies to all files being loaded by the current LOAD TABLE statement. It's not possible to load from a combination of encrypted and non-encrypted files in the same statement.

  CHECK CONSTRAINTS \{ ON | OFF \}
 :   Evaluates check constraints, which you can ignore or log. CHECK CONSTRAINTS defaults to ON.

    Setting CHECK CONSTRAINTS OFF causes data lake Relational Engine to ignore all check constraint violations. This can be useful, for example, during database rebuilding. If a table has check constraints that call user-defined functions that are not yet created, the rebuild fails unless this option is set to OFF.

    This option is mutually exclusive to the following options. If any of these options are specified in the same load, an error results:

    -   IGNORE CONSTRAINT ALL
    -   IGNORE CONSTRAINT CHECK
    -   LOG ALL
    -   LOG CHECK

  DEFAULTS \{ ON | OFF \}
 :   Uses a column's default value. This option is ON by default. If the DEFAULTS option is OFF, any column not present in the column list is assigned NULL.

    The setting for the DEFAULTS option applies to all column default values, including AUTOINCREMENT.

  QUOTES \{ ON | OFF \}
 :   Indicates that input strings are enclosed in quote characters. QUOTES is an optional clause and is ON by default. The first such character encountered in a string is treated as the quote character for the string. String data must be terminated with a matching quote.

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
    -   Not supported for FORMAT parquet.

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


  QUOTE *<enclosure-character\>*
 :   For TEXT data only; identifies the enclosure character to be placed around string values. If not specified, the default QUOTE character is either a single \('\) or double \("\) quotation mark, depending on what is used in the field. If QUOTES OFF is defined, QUOTE is ignored.

    If the specified *<enclosure-character\>* is multibyte, only the first byte is used; the remaining bytes are ignored.

    Not supported for FORMAT parquet.

  QUOTE ESCAPE '*<escape-character\>*'
 :   Specifies the escape character used in the data. If not specified, the default QUOTE ESCAPE character is the value of QUOTE. For example, if QUOTE is defined as percent \(%\), but QUOTE ESCAPE is not defined, the default value for QUOTE ESCAPE becomes %. If neither QUOTE ESCAPE nor QUOTE are defined, QUOTE defaults to either a single \('\) or double \("\) quotation mark, depending on what is used in the field, and QUOTE ESCAPE defaults to match QUOTE.

    If the specified ESCAPE character is multibyte, only the first byte is used; the remaining bytes are ignored.

    If QUOTES ON and QUOTE ESCAPE is not defined, single quote becomes the ESCAPE character and must be escaped by another quote.

    Not supported for FORMAT parquet.

  ESCAPES
 :   If you omit a *<column-spec\>* definition for an input field and ESCAPES is ON \(the default\), characters following the backslash character are recognized and interpreted as special characters by the database server. You can include newline characters as the combination \\n, and other characters as hexadecimal ASCII codes, such as \\x09 for the [Tab\] character. A sequence of two backslash characters \( \\\\ \) is interpreted as a single backslash.

    > ### Note:  
    > For data lake Relational Engine, you need to set ESCAPES OFF.

  FORMAT \{ ascii | binary | bcp | csv | parquet \}
 :    ascii | binary
 :   These formats are defined by *<column-spec\>*. If you omit that definition for a column, by default data lake Relational Engine uses the format defined by this option. Input lines are assumed to have ASCII \(the default\) or binary fields, one row per line, with values separated by the column delimiter character.

  bcp
 :   -   The BCP data file loaded into data lake Relational Engine tables must be exported \(BCP OUT\) in cross-platform file format using the -c option.
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


      csv
     :   A row in a CSV file must be terminated either by a row deliminator \(default newline\) or a column deliminator \(default coma\) followed by a row delimiter. The maximum size of a delimiter is 4 bytes. An error message appears if the deliminator exceeds 4 bytes.

        A CSV file may contain partial rows, defined as any row with the number of fields less than the number of columns specified \(either explicitly or implicitly\). All fields missing from a partial row are assigned a NULL value. If the column is not nullable, an error message appears, and no data is imported.

        If a table has K columns, a CSV file has M fields, and the LOAD TABLE statement indicates N columns \(either explicitly or implicitly\), when N <= K and N < M, columns missing from the column list in the load statement are assigned default values.

      parquet
     :   To load a Parquet format file into a table, use the FORMAT parquet clause and specify `.parquet` or `.parq` as the file name extension.

        Not all LOAD TABLE clauses work with FORMAT parquet; some are ignored, while others can cause the LOAD TABLE statement to roll back. See [Loading Parquet Files](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/a054ac0ce09e47799e5f24860378056b.html "Parquet is an efficient, open-source, column-oriented format file designed for Apache Hadoop. You can load tables in Parquet format using the data lake Relational Engine LOAD TABLE statement.") :arrow_upper_right: in *SAP HANA Cloud, Data Lake Load and Unload Management* for details.

   DELIMITED BY '*<string\>*'
 :   If you omit a column delimiter in the *<column-spec\>* definition, the default column delimiter character is a comma. You can specify an alternative column delimiter by providing a single ASCII character or the hexadecimal character representation. The DELIMITED BY clause is:

    ```
    ... DELIMITED BY '\x09' ...
    ```

    To use the newline character as a delimiter, you can specify either the special combination '\\n' or its ASCII value '\\x0a'. Although you can specify up to four characters in the *<column-spec\>* *<delimiter-string\>*, you can specify only a single character in the DELIMITED BY clause.

    When specifying the DATE column with the NULL clause, the date column is treated as a variable-width date field if DELIMITED BY clause is included. Otherwise, date column is treated as fixed-width date field.

    Not supported for FORMAT parquet.

  STRIP \{ OFF | RTRIM \}
 :   Determines whether unquoted values should have trailing blanks stripped off before they are inserted. These STRIP keywords are accepted:

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

  BYTE ORDER \{ NATIVE | LOW | HIGH \}
 :   Specifies the byte order during reads. This option applies to all binary input fields. You cannot set different BYTE ORDER options for individual files. If no BYTE ORDER is defined, the default is NATIVE. You can specify:

    -   NATIVE – \(default\)data lake Relational Engine always reads binary data in the format native to the machine it is running on.
    -   HIGH – when multibyte quantities have the high-order byte first \(for big-endian platforms\).
    -   LOW – when multibyte quantities have the low-order byte first \(for little-endian platforms\).

    Not supported for FORMAT parquet.

  LIMIT *<number-of-rows\>*
 :   Specifies the maximum number of rows to insert into the table. The default is 0 for no limit. The maximum is 2<sup>31</sup> - 1 \(2147483647\) rows.

  NOTIFY *<number-of-rows\>*
 :   Specifies that you be notified with a message each time the specified number of rows is successfully inserted into the table. The default is 0, meaning no notifications are printed. The value of this option overrides the value of the NOTIFY\_MODULUS database option.

  ON FILE ERROR \{ ROLLBACK | FINISH | CONTINUE \}
 :   Specifies the action data lake Relational Engine takes when an input file cannot be opened because it does not exist or you have incorrect privileges to read the file. You can specify one of the following:

    -   ROLLBACK – returns an error and aborts the entire transaction \(the default\).
    -   FINISH – finishes the insertions already completed and ends the load operation.
    -   CONTINUE – skips the file to continue the load operation.

    Only one ON FILE ERROR clause is permitted.

  PREVIEW \{ ON | OFF \}
 :   Displays the layout of input into the destination table including starting position, name, and data type of each column. Data lake Relational Engine displays this information at the start of the load process. If you are writing to a log file, this information is also included in the log.

  ROW DELIMITED BY '*<delimiter-string\>*'
 :   Specifies a string up to 4 bytes in length that indicates the end of an input record. You can use this option only if all fields within the row are any of the following:

    -   Delimited with column terminators
    -   Data defined by the DATE or DATETIME *<column-spec\>* options
    -   ASCII fixed-length fields

    Always include ROW DELIMITED BY to ensure parallel loads. Omitting this clause from the LOAD specification may cause data lake Relational Engine to load serially rather than in parallel.

    You cannot use this clause if any input fields contain binary data. With this clause, a row terminator causes any missing fields to be set to NULL. All rows must have the same row delimiters, and it must be distinct from all column delimiters. The row and field delimiter strings cannot be an initial subset of each other. For example, you cannot specify "\*" as a field delimiter and "\*\#" as the row delimiter, but you could specify "\#" as the field delimiter with that row delimiter.

    If a row is missing its delimiters, data lake Relational Engine returns an error and rolls back the entire load transaction. The only exception is the final record of a file where it rolls back that row and returns a warning message.

    Not supported for FORMAT parquet.

  SKIP *<number-of-rows\>*
 :   Defines the number of rows to skip at the beginning of the input tables for this load. The maximum number of rows to skip is 2<sup>31</sup> - 1 \(2147483647\). The default is 0. SKIP runs in single-threaded mode as it reads the rows to skip.

    The FORMAT parquet clause does not support SKIP *<number-of-rows\>* and will return an error and roll back the LOAD TABLE statement, if specified.

  HEADER SKIP \[ALL\] *<number\>* … HEADER DELIMITED BY '*<string\>*'
 :   When you include ALL in your load statement for a multiple-file load, LOAD TABLE skips the number of header rows \(that you specify with *<number\>*\) from the start of each file, while omitting ALL just skips the number of header rows from just the first file. ALL does not change the results for a single-file load.

    HEADER SKIP *<number\>*, without ALL, specifies a number of lines at the beginning of the data file, including header rows, for LOAD TABLE to skip. All LOAD TABLE column specifications and other load options are ignored, until the specified number of rows is skipped.

    -   The number of lines to skip is greater than or equal to zero.
    -   Lines are determined by a 1-to-4-character delimiter string specified in the HEADER DELIMITED BY clause. The default HEADER DELIMITED BY string is the \\n character.
    -   The HEADER DELIMITED BY string has a maximum length of four characters. An error is returned, if the string length is greater than four or less than one.
    -   When a non-zero HEADER SKIP value is specified, all data inclusive of the HEADER DELIMITED BY delimiter is ignored, until the delimiter is encountered the number of times specified in the HEADER SKIP clause.
    -   All LOAD TABLE column specifications and other load options are ignored, until the specified number of rows has been skipped. After the specified number of rows has been skipped, the LOAD TABLE column specifications and other load options are applied to the remaining data.
    -   The "header" bytes are ignored only at the beginning of the data. When multiple files are specified in the USING clause, HEADER SKIP only ignores data starting from the first row of the first file, until it skips the specified number of header rows, even if those rows exist in subsequent files. LOAD TABLE does not look for headers once it starts parsing actual data.
    -   No error is reported, if LOAD TABLE processes all input data before skipping the number of rows specified by HEADER SKIP.
    -   When you specify FORMAT parquet in the LOAD TABLE statement, data lake Relational Engine ignores the HEADER SKIP \[ALL\] clause and issues a message with this information.

    HEADER SKIP ALL has the following behaviors:

    -   You cannot specify HEADER SKIP and HEADER SKIP ALL in the same LOAD TABLE statement; doing so results in an error.
    -   You can specify HEADER SKIP ALL *<number\>* and SKIP *<number-of-rows\>* together. When you do, the number of header rows \(specified in *<number\>*\) is skipped first, then SKIP *<number-of-rows\>* is performed until the statement reaches the number of rows you specified.
    -   You can specify HEADER SKIP ALL *<number\>* and LIMIT *<number-of-rows\>*. When you do, the number of header rows \(specified in *<number\>*\) is skipped first, then rows are loaded for the number of rows you specify.

  WORD SKIP *<number\>*
 :   Allows the load to continue when it encounters data longer than the limit specified when the word index was created.

    If a row is not loaded because a word exceeds the maximum permitted size, a warning is written to the `.iqmsg` file. WORD size violations can be optionally logged to the MESSAGE LOG file and rejected rows logged to the ROW LOG file specified in the LOAD TABLE statement.

    -   If the option is not specified, LOAD TABLE reports an error and rolls back on the first occurrence of a word that is longer than the specified limit.
    -   *<number\>* specifies the number of times the “***Words exceeding the maximum permitted word length not supported***” error is ignored.
    -   0 \(zero\) means there is no limit.

  ON PARTIAL INPUT ROW \{ ROLLBACK | CONTINUE \}
 :   Specifies the action to take when a partial input row is encountered during a load. You can specify one of the following:

    -   CONTINUE – \(default\) issues a warning and continues the load operation.
    -   ROLLBACK – aborts the entire load operation and reports the error:

        ```
        Partial input record skipped at EOF.
        SQLSTATE: QDC32    SQLSTATE: -1000232L
        ```


    Not supported for FORMAT parquet.

  IGNORE CONSTRAINT *<constraint-type\>* *<string\>*
 :   Specifies whether to ignore CHECK, UNIQUE, NULL, DATA VALUE, and FOREIGN KEY integrity constraint violations that occur during a load. *<string\>* is an integer that indicates the maximum number of violations to ignore before initiating a rollback. Specifying each *<constraint-type\>* has the following result:

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

  MESSAGE LOG '*<string\>*'\] \[ROW LOG '*<string\>*'
 :   Specifies the names of files in which to log information about integrity constraint violations and the types of violations to log. Timestamps indicating the start and completion of the load are logged in both the MESSAGE LOG and the ROW LOG files. Both MESSAGE LOG and ROW LOG must be specified, or no information about integrity violations is logged.

    -   If the ONLY LOG clause is not specified, no information on integrity constraint violations is logged. Only the timestamps indicating the start and completion of the load are logged.
    -   Information is logged on all integrity constraint-type violations specified in the ONLY LOG clause or for all word index-length violations if the keyword WORD is specified.
    -   If constraint violations are being logged, every occurrence of an integrity constraint violation generates exactly one row of information in the MESSAGE LOG file.

        The number of rows \(errors reported\) in the MESSAGE LOG file can exceed the IGNORE CONSTRAINT option limit, because the load is performed by multiple threads running in parallel. More than one thread might report that the number of constraint violations has exceeded the specified limit.

    -   If constraint violations are being logged, exactly one row of information is logged in the ROW LOG file for a given row, regardless of the number of integrity constraint violations that occur on that row.

        The number of distinct errors in the MESSAGE LOG file might not exactly match the number of rows in the ROW LOG file. The difference in the number of rows is due to the parallel processing of the load described above for the MESSAGE LOG.

    -   The MESSAGE LOG and ROW LOG files cannot be raw partitions or named pipes.
    -   If the MESSAGE LOG or ROW LOG file already exists, new information is appended to the file.
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

  LOG DELIMITED BY
 :   Specifies the separator between data values in the ROW LOG file. The default separator is a comma.

    Data lake Relational Engine no longer returns an error message when FORMAT bcp is specified as a LOAD TABLE clause. In addition, these conditions are verified and proper error messages are returned:

  ALLOW MISSING COLUMNS \{ ON | OFF \}
 :   Determines the behavior when one or more columns in the LOAD TABLE statement cannot be matched with a column in a given file. The default value is OFF. When this clause is OFF, the statement fails if a column cannot be matched.

    When this clause is ON, columns that cannot be matched are populated with the column's default value. If no default value is defined, NULL values are loaded. If the column has no default value and is defined as NOT NULL, the statement fails. Use the MISSING DEFAULT column option to specify a default value to use when the column cannot be matched.

  WITH MATCHING COLUMN NAMES
 :   \(Applies to FORMAT parquet only\) Specifies that the column names in the data lake Relational Engine table match the column names in the Parquet files being loaded. This is equivalent to specifying FROM COLUMN '*<iq-column-name\>*' for each column in the load specification. For example, the following two statements are equivalent:

    ```
    LOAD INTO TABLE T (
    	temperature,
    	humidity,
    	ts )
        FROM 'file1.parquet'
        WITH MATCHING COLUMN NAMES
        FORMAT PARQUET
        ESCAPES OFF;
    
    LOAD INTO TABLE T (
    	temperature FROM COLUMN 'temperature',
    	humidity FROM COLUMN 'humidity',
    	ts FROM COLUMN 'ts' )
        FROM 'file1.parquet'
        FORMAT PARQUET
        ESCAPES OFF ;
    ```

    You can override individual columns by specifying FROM COLUMN for those columns.

 

<a name="loio7ca3f60902f3473296cb309533d89210__load_table_remarks1"/>

## Remarks

The LOAD TABLE statement allows efficient mass insertion into a database table from multiple file types.

The LOAD TABLE clauses also let you control load behavior when integrity constraints are violated and to log information about the violations.

You can use LOAD TABLE on a temporary table, but the temporary table must have been declared with ON COMMIT PRESERVE ROWS, or the next COMMIT removes the rows you've loaded.

LOAD TABLE supports loading of large object \(LOB\) data.



### Error Messages

-   If the specified load format isn't ascii, binary, bcp, or csv data lake Relational Engine returns the message “***Only ASCII, BCP, BINARY, PARQUET, and CSV are supported LOAD formats.***”
-   If the LOAD TABLE column specification contains anything other than column name, NULL, or ENCRYPTED, then data lake Relational Engine returns the error message “***Invalid load specification for LOAD ... FORMAT BCP.***”
-   If the column delimiter or row terminator size for the FORMAT bcp load is greater than 10 characters, then data lake Relational Engine returns the message “***Delimiter '%2' must be 1 to %3 characters in length.***” \(where %3 equals 10\).

    Messages corresponding to error or warning conditions, which can occur for FORMAT bcp as well as FORMAT ascii, are the same for both formats.

-   If the load default value specified is AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT, data lake Relational Engine returns the error “***Default value %2 cannot be used as a LOAD default value. %1***”
-   If the LOAD TABLE specification doesn't contain any columns that need to be loaded from the file specified, data lake Relational Engine returns the error “***The LOAD statement must contain at least one column to be loaded from input file.***” and the LOAD TABLE statement rolls back.
-   If a load exceeds the limit on the maximum number of terms for a text document with TEXT indexes, data lake Relational Engine returns the error “***Text document exceeds maximum number of terms. Support up to 4294967295 terms per document.***”



### Column Options

For ASCII, BINARY, CSV and BCP formats, data lake Relational Engine supports both character and binary data and it support both fixed- and variable-length formats. To handle all of these formats, you supply a *<load-specification\>* to tell data lake Relational Engine what kind of data to expect from each “column” or field in the source file. The *<column-spec\>* lets you define these formats:

-   ASCII with a fixed length of bytes. The *<input-width\>* value is an integer indicating the fixed width in bytes of the input field in every record.
-   Binary or nonbinary fields that use a PREFIX clause, which comprises two parts:


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


    If you plan to use PREFIX *<n\>* BINARY for a varchar or varbinary column for a file that was generated by the binary mode option for extraction, use the TEMP\_EXTRACT\_LENGTH\_PREFIX option for extraction to specify the length of the prefix portion, and TEMP\_EXTRACT\_VARYING to extract the associated data portion with a variable length of actual data \(instead of the declared length of varchar/varbinary\). Specifying TEMP\_EXTRACT\_VARYING allows you to extract the varchar or varbinary column without trailing padding in the extracted file. With PREFIX *<n\>* BINARY, trailing blanks for the varchar column \(and trailing zeros for the varbinary column\) aren't stripped from values when inserted into the column.

    If the data is unloaded using the extraction facility with the TEMP\_EXTRACT\_BINARY option set ON, you must use the BINARY WITH NULL BYTE parameter for each column when you load the binary data.

    > ### Note:  
    > When you extract data to cloud storage in binary format, ensure that you use the BINARY *<data-type\>* WITH NULL BYTE or BINARY WITH NULL BYTE parameter for each column at load time.

    When loading binary data, you can specify the data type of the input file. Defining the data type can help you avoid conversion errors if an unexpected data type change occurs for the column. If you don't specify *<data-type\>* in the BINARY WITH NULL BYTE parameter, data lake assumes the input field has the same data type as the column.

-   Variable-length characters delimited by a separator. You can specify the terminator as hexadecimal ASCII characters and the bytes \(1, 2, or 4\) to specify the length of the input. This *<delimiter-string\>* variable-length characters, delimited by a separator, can be any string of up to 4 characters, including any combination of printable characters, and any 8-bit hexadecimal ASCII code that represents a nonprinting character. For example, specify:

    -   "\\x09" to represent a tab as the terminator.
    -   "\\x00" for a null terminator \(no visible terminator as in “C” strings\).
    -   "\\x0a" for a newline character as the terminator. You can also use the special character combination of '\\n' for newline.

    > ### Note:  
    > The delimiter string can be from 1 to 4 characters long, but you can specify only a single character in the DELIMITED BY clause. For BCP, the delimiter can be up to 10 characters.

-   DATE or DATETIME string as ASCII characters. You need to define the *<input-date-format\>* or *<input-datetime-format\>* of the string using one of the corresponding formats for the date and datetime data types supported by data lake Relational Engine. Use DATE for DATE values and DATETIME for DATETIME and TIME values. Formatting dates and times are:


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

    Represents number of year. Default is current year.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    mm or MM


    
    </td>
    <td valign="top">

    Represents number of month. Always use leading zero or blank for number of the month where appropriate, for example, '05' for May. DATE value must include a month. For example, if the DATE value you enter is 1998, you receive an error. If you enter '03', data lake Relational Engine applies the default year and day and converts it to '1998-03-01'.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    dd or DD

    jjj or JJJ


    
    </td>
    <td valign="top">

    Represents number of day. Default day is 01. Always use leading zeros for number of day where appropriate, for example, '01' for first day. J or j indicates a Julian day \(1 to 366\) of the year.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    hh or HH


    
    </td>
    <td valign="top">

    Represents hour. Hour is based on 24-hour clock. Always use leading zeros or blanks for hour where appropriate, for example, '01' for 1 am. '00' is also valid value for hour of 12 a.m.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    nn


    
    </td>
    <td valign="top">

    Represents minute. Always use leading zeros for minute where appropriate, for example, '08' for 8 minutes.


    
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

    Represents the p.m. designation only if needed.


    
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

Use the VALUE option to specify a load default column value. You can load a default value into a column, even if the column doesn't have a default value defined in the table schema. This feature provides more flexibility at load time.

-   The LOAD TABLE DEFAULTS option must be ON in order to use the default value specified in the LOAD TABLE statement. If the DEFAULTS option is OFF, the specified load default value is used and a NULL value is inserted into the column instead.
-   The LOAD TABLE statement must contain at least one column that needs to be loaded from the file specified in the LOAD TABLE statement. Otherwise, an error is reported and the load is performed.
-   The specified load default value must conform to the supported default values for columns and default value restrictions. The LOAD TABLE DEFAULT option doesn't support AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT as a load default value.
-   The LOAD TABLE VALUE *<default-value\>* must be of the same character set as that of the database.
-   Encryption of the default value isn't supported for the load default values specified in the LOAD TABLE VALUE clause.
-   A constraint violation caused by evaluation of the specified load default value is counted for each row that is inserted in the table.

Use the MISSING DEFAULT option to specify a default column value to use if the column cannot be matched with a column in the loaded file. This option only applies when ALLOW MISSING COLUMNS is ON.

Another important part of the *<load-specification\>* is the FILLER option. This option indicates you want to skip over a specified field in the source input file. For example, there may be characters at the end of rows or even entire fields in the input files that you don't want to add to the table. As with the *<column-spec\>* definition, FILLER specifies ASCII fixed length of bytes, variable length characters delimited by a separator, and binary fields using PREFIX bytes.



### Parquet Files

By default, data lake Relational Engine loads data from Parquet files into a table using the column order in the file: the first column in the Parquet file is loaded into the first column in the LOAD TABLE statement, and so on. Use the FROM COLUMN syntax to override this order with a specific column in the Parquet file, using either the column name or column number \(1-origin\). Case-sensitive column names are preferred when matching, but if there are no case-sensitive matches, case-insensitive names are matched. If there are multiple matches in either step of matching, the statement fails. If there are no matches, the statement may fail depending on the ALLOW MISSING COLUMNS settings.

Specifying FROM COLUMN overrides WITH MATCHING COLUMN NAMES for that column.

When you specify FROM COLUMN for a column, that column still occupies its position when determining which data is loaded into other columns:

```
LOAD INTO TABLE T (
	time_stamp, -- Column 1
	humid FROM COLUMN 'humidity', -- Column 2, overridden
	temp, -- Column 3 )
FROM 'file1.parquet'
FORMAT parquet
ESCAPES OFF ;
```

In this example, temp still gets data from the third column in the Parquet file because it is the third column in the statement.

When you specify FORMAT parquet in the LOAD TABLE statement, data lake Relational Engine ignores the following *<column-spec\>* options and issues a message with this information:

```
ASCII ( <input-width> )
```

```
PREFIX { 1 | 2 | 4 }
```

```
BINARY [ WITH NULL BYTE ]
```

```
PREFIX { 1 | 2 | 4 } BINARY [ WITH NULL BYTE ] [ VARYING ]
```

```
'<delimiter-string>'
```

The FORMAT parquet clause doesn't support the following *<load-specification\>* options. If you specify both, data lake Relational Engine returns an error and rolls back the LOAD TABLE statement:

```
FILLER <filler-type>
```

```
<filler-type> ::=
    { <input-width>
     | PREFIX { 1 | 2 | 4 }
     | '<delimiter-string>'
      }
```



<a name="loio7ca3f60902f3473296cb309533d89210__load_table_privileges1"/>

## Privileges



### 

To LOAD tables and views requires one of:

-   You own the object.
-   LOAD ANY TABLE system privilege
-   ALTER ANY TABLE system privilege
-   ALTER ANY OBJECT system privilege
-   LOAD or ALTER object-level privilege on the object
-   If the object is in a schema that is owned by another, then LOAD or ALTER object-level privilege on the schema containing the object.

LOAD TABLE also requires a write lock on the table. When using the USING CLIENT FILE clause, you require:

-   READ CLIENT FILE system privilege
-   Read privileges on the directory being read from
-   The ALLOW\_READ\_CLIENT\_FILE database option is enabled

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loio7ca3f60902f3473296cb309533d89210__load_table_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not applicable



<a name="loio7ca3f60902f3473296cb309533d89210__load_table_examples1"/>

## Examples

**Example 1:** This example loads 14 columns into table T1 from the object `MULTI.DAT`.

Example 1 syntax for Azure:

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

Example 1 syntax for Amazon S3:

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

Example 1 syntax for SAP Converged Cloud, which is an S3-compliant provider:

```
LOAD TABLE T1
    ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
    USING FILE 's3://sap-hanadatalake/hdl_folder/nations.csv'
    ROW DELIMITED BY '\x0a'
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
	   REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap' 
    ESCAPES OFF;
```

\(DEPRECATED\) Example 1 syntax for Amazon S3:

```
LOAD TABLE T1
    ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
    USING FILE 's3://MY_BUCKET_1/MULTI.DAT'
    ROW DELIMITED BY '\x0a'
    ACCESS_KEY_ID 'DNLDLRVIRGQQ9EXAMPLE'
    SECRET_ACCESS_KEY 'CMKCKQUHQFPP8EXAMPLE/123abc/Example12'
    REGION 'us-east-2'
    ESCAPES OFF;
```

Example 1 syntax for Google Cloud:

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

Example 2 syntax for Azure:

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

Example 2 syntax for Amazon S3:

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

Example 2 syntax for SAP Converged Cloud, which is an S3-compliant provider:

```
LOAD TABLE T2
    ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
    USING FILE 's3://sap-hanadatalake/hdl_folder/COMPRESSED.GZ'
    ROW DELIMITED BY '\x0a'
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
	   REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap' 
    ESCAPES OFF;
```

\(DEPRECATED\) Example 2 syntax for Amazon S3:

```
LOAD TABLE T2
    ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
    USING FILE 's3://MY_BUCKET_2/COMPRESSED.GZ'
    ROW DELIMITED BY '\x0a'
    ACCESS_KEY_ID 'DNLDLRVIRGQQ9EXAMPLE'
    SECRET_ACCESS_KEY 'CMKCKQUHQFPP8EXAMPLE/123abc/Example12'
    REGION 'us-east-2'
    ESCAPES OFF;
```

Example 2 syntax for Google Cloud:

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

Example 3 syntax for Azure:

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

Example 3 syntax for Amazon S3:

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

Example 3 syntax for SAP Converged Cloud, which is an S3-compliant provider:

```
LOAD TABLE T3
    ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
    USING FILE 's3://sap-hanadatalake/hdl_folder/PART_1_1.DAT','s3://sap-hanadatalake/hdl_folder/PART_2_1.DAT','s3://sap-hanadatalake/hdl_folder/PART_3_1.DAT'
    DELIMITED BY '|'
    ROW DELIMITED BY '\x0a'
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
	   REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap'
    ESCAPES OFF;
```

\(DEPRECATED\) Example 3 syntax for Amazon S3:

```
LOAD TABLE T3
    ( C1, C2, C3, C4, C5, C6, C7, C8, C9, C10, C11, C12, C13, C14 )
    USING FILE 's3://MY_BUCKET_3/PART_1_1.DAT','s3://MY_BUCKET_3/PART_2_1.DAT','s3://MY_BUCKET_3/PART_3_1.DAT'
    DELIMITED BY '|'
    ROW DELIMITED BY '\x0a'	
    ACCESS_KEY_ID 'DNLDLRVIRGQQ9EXAMPLE'
    SECRET_ACCESS_KEY 'CMKCKQUHQFPP8EXAMPLE/123abc/Example12'
    REGION 'us-east-2'
    ESCAPES OFF;
```

Example 3 syntax for Google Cloud:

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

Example 4 syntax for Azure:

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

Example 4 syntax for Amazon S3:

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

Example 4 syntax for SAP Converged Cloud, which is an S3-compliant provider:

```
LOAD TABLE T4
    ( C1 BINARY WITH NULL BYTE, C2 BINARY WITH NULL BYTE, C3 BINARY WITH NULL BYTE, C4 BINARY WITH NULL BYTE, C5 BINARY WITH NULL BYTE )
    USING FILE 's3://sap-hanadatalake/hdl_folder/MULTI.DAT'
    FORMAT BINARY
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
	   REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap'
    ESCAPES OFF;
```

\(DEPRECATED\) Example 4 syntax for Amazon S3:

```
LOAD TABLE T4 
    ( C1 BINARY WITH NULL BYTE, C2 BINARY WITH NULL BYTE, C3 BINARY WITH NULL BYTE, C4 BINARY WITH NULL BYTE, C5 BINARY WITH NULL BYTE )
    USING FILE 's3://MY_BUCKET_4/MULTI.DAT'
    FORMAT BINARY
    ACCESS_KEY_ID 'DNLDLRVIRGQQ9EXAMPLE'
    SECRET_ACCESS_KEY 'CMKCKQUHQFPP8EXAMPLE/123abc/Example12'
    REGION 'us-east-2'
    ESCAPES OFF;
```

Example 4 syntax for Google Cloud:

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

Example 5 syntax for Azure:

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

Example 5 syntax for Amazon S3:

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

Example 5 syntax for SAP Converged Cloud, which is an S3-compliant provider:

```
LOAD TABLE T5
    (C1,C2,C3 ASCII FILE (',') NULL('NULL'),C4 BINARY FILE (',') NULL('NULL'))
    USING FILE 's3://sap-hanadatalake/hdl_folder/MY_TEST_.IMP'
    ROW DELIMITED BY '\X0A'
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
	   REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap'
    ESCAPES OFF;
```

\(DEPRECATED\) Example 5 syntax for Amazon S3:

```
LOAD TABLE T5 (C1,C2,C3 ASCII FILE (',') NULL('NULL'),C4 BINARY FILE (',') NULL('NULL'))
    FROM 's3://MY_BUCKET_5/DATA/MY_TEST_.IMP'
    ROW DELIMITED BY '\X0A'
    ACCESS_KEY_ID 'AKIAXE6MOCNLEXAMPLE'
    SECRET_ACCESS_KEY 'iKsQvq4Mbh6zhcxJcAxEXAMPLEEXAMPLE'
    REGION 'us-east-2'
    QUOTES OFF 
    ESCAPES OFF;
```

Example 5 syntax for Google Cloud:

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

**Example 6:** This example loads a Parquet file. The statement loads five columns into table T6 from Parquet file `MULTI.PARQUET`.

Example 6 syntax for Azure:

```
LOAD TABLE T6 
    ( C1, C2, C3, C4, C5 )
    FROM 'bb://MY_AZURE_CONTAINER_6/MULTI.PARQUET'
    FORMAT PARQUET
    CONNECTION_STRING 'DefaultEndpointsProtocol=https;AccountName=example;
        AccountKey=example_key;
        EndpointSuffix=core.windows.net'
    ESCAPES OFF;
```

Example 6 syntax for Amazon S3:

```
LOAD TABLE T6 
    ( C1, C2, C3, C4, C5 )
    FROM 's3://MY_BUCKET_6/MULTI.PARQUET'
    FORMAT PARQUET
    CONNECTION_STRING 'ACCESS_KEY_ID=xyz;
        SECRET_ACCESS_KEY=abc;
        REGION=eu-central-1;
        SESSION_TOKEN=pqr'
    ESCAPES OFF;
```

Example 6 syntax for SAP Converged Cloud, which is an S3-compliant provider:

```
LOAD TABLE T6
    ( C1, C2, C3, C4, C5 )
    USING FILE 's3://sap-hanadatalake/hdl_folder/MULTI.PARQUET'
    FORMAT PARQUET
    CONNECTION_STRING 'ACCESS_KEY_ID=ftwbaebtwjomo;
        SECRET_ACCESS_KEY=fomoicymiimhoidc;
        ENDPOINT_TYPE=PATH;
	   REGION=eu-de-1;
        ENDPOINT=https://objectstore-3.eu-de-1.cloud.sap'
    ESCAPES OFF;
```

\(DEPRECATED\) Example 6 syntax for Amazon S3:

```
LOAD TABLE T6 
    ( C1, C2, C3, C4, C5 )
    FROM 's3://MY_BUCKET_6/MULTI.PARQUET'
    FORMAT PARQUET
    ACCESS_KEY_ID 'DNLDLRVIRGQQ9EXAMPLE'
    SECRET_ACCESS_KEY 'CMKCKQUHQFPP8EXAMPLE/123abc/Example12'
    REGION 'us-east-2'
    ESCAPES OFF;
```

Example 6 syntax for Google Cloud:

```
LOAD TABLE T6 
    ( C1, C2, C3, C4, C5 )
    FROM 'gs://MY_BUCKET_6/MULTI.PARQUET'
    FORMAT PARQUET
    CONNECTION_STRING 'client_email=XXXXXXXX;
    private_key=-----BEGIN PRIVATE KEY-----\nXXXXXXXX\n-----END PRIVATE KEY-----\n;
    private_key_id=XXXXXXXX'
    ESCAPES OFF;
```

Example 7 syntax showing LOAD from data lake Files:

```
LOAD TABLE T7
    (c1) 
    FROM 'hdlfs:///employeelist.csv'
    ESCAPES OFF;  
```

This example loads data from a file `abcd.inp` on a client computer:

```
LOAD TABLE t1(c1,c2,FILLER(30))
    USING CLIENT FILE 's3://MY_BUCKET_6/abcd.inp'
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

This example loads data from two files into the product\_new table \(which allows NULL values\). The tab character is the default column delimiter, and the newline character is the row delimiter:

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

This example ignores 10 word-length violations; on the 11th, it deploys the new error and rolls back the load:

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

This example loads data into table t1 from the BCP character file `bcp_file.bcp` using the FORMAT BCP load option:

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

This example loads default values 12345 into c1 using the VALUE load option, and load c2 and c3 with data from the `LoadConst04.dat` file:

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

This example loads c1 and c2 with data from the file `bcp_file.bcp` using the FORMAT BCP load option and set c3 to the value 10:

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

This code fragment ignores one header row at the beginning of the data file, where the header row is delimited by '&&':

```
LOAD TABLE
...HEADER SKIP 1 HEADER DELIMITED by '&&'
...
```

This code fragment ignores 2 header rows at the beginning of the data file, where each header row is delimited by '\\n':

```
LOAD TABLE
...HEADER SKIP 2
...
```

This example loads a table from a CSV file, using a double quotation mark for the QUOTE enclosure character and the backslash \(\\\) for the QUOTE ESCAPE character.

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

c1 c2 c3

" \\\\ \\abc

\\a\\b\\c \\\\\\\\ "dog"

This example loads a table, inserting the names of the files \(`DATAFILE1.CSV` and `DATAFILE2.CSV`\) into the c2 column as specified by FILE NAME:

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

In this example, the contents of `datefile1.csv` are:

```
c1_val1, c3_value1,
c1_val2, c3_value2,
```

The contents of `datefile2.csv` are:

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

This example loads a table named test2 \(which contains columns c1 and c2, both of which are VARCHAR\(20\)\), using files `datafile1.csv` and `datafile2.csv`, skipping the first header row from the start of each file:

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

In this example, the contents of `datefile1.csv` are:

```
c1_val1, c3_value1,
c1_val2, c3_value2,
```

The contents of `datefile2.csv` are:

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

To execute a VARCHAR or VARBINARY load from a file generated by the data extraction facility, without specifying the TEMP\_EXTRACT\_LENGTH\_PREFIX option:

```
LOAD TABLE t1 (c1 BINARY WITH NULL BYTE) FROM 'yyy' FORMAT BINARY
```

You can specify this LOAD *<column-spec\>*, binary, for any column data type — the column in this example is c1.

This example uses the prefix *<n\>* binary option to specify a VARCHAR or VARBINARY load from a file generated by the data extraction facility using the TEMP\_EXTRACT\_LENGTH\_PREFIX option set to 2, where c1 is a VARCHAR column:

```
LOAD TABLE t1 (c1 PREFIX 2 BINARY WITH NULL BYTE) FROM 'xxx' FORMAT BINARY
```

You can only specify prefix *<n\>* binary for VARCHAR and VARBINARY columns; which in this example is c1.

This example loads three Parquet files into a table, using two load groups to handle differences in column names between the files:

```
LOAD INTO TABLE T (
    temperature FROM COLUMN 'Temperature',
    Humidity FROM COLUMN 'Humidity',
    ts FROM COLUMN 'Time'
) 
    FROM file1.parquet, file3.parquet
( 
    humidity FROM COLUMN 'Humidity',
    temperature FROM COLUMN Temperature',
    ts FROM COLUMN 'Timestamp'  
) 
    FROM file2.parquet
    FORMAT PARQUET
    ESCAPES OFF ;
```

**Related Information**  


[LOAD TABLE Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/97f011fc1d834d8ea920911caa9638f2.html "Imports data into a data lake Relational Engine database table from either the external object store (Azure BLOB storage, an Amazon S3 bucket, S3-compliant bucket, or a Google Cloud Storage) or from data lake Files containers (the managed object store).") :arrow_upper_right:

[SAP HANA Cloud, Data Lake Load and Unload Management](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/e77c96193a604e05ba198e424de2ed6c.html "Data load (import) and export (unload) procedures for data lake Relational Engine, including loading from and unloading to data lake Files.") :arrow_upper_right:

[Loading Data from Azure Blob Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/e52d8274e0364e868fd02ec3c2b3ed9c.html "Use the data lake Relational Engine LOAD TABLE statement to load data into a data lake Relational Engine table from Azure Blob storage.") :arrow_upper_right:

[Loading Data from the Amazon S3 Bucket](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/9e9a558cf14a44bc812e2562afcd116f.html "Use the LOAD TABLE statement to load data into a data lake Relational Engine table from your Amazon S3 bucket.") :arrow_upper_right:

[Loading Data from Google Cloud Storage](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/a723d42f6c3d4d5ab9f2a1424130d10c.html "Use the LOAD TABLE statement to load data into a data lake Relational Engine table from your Google Cloud Storage bucket.") :arrow_upper_right:

[Loading Data From Data Lake Files to Data Lake Relational Engine](https://help.sap.com/viewer/b239ed4bb73a4f07886657e237f1875f/2023_1_QRC/en-US/ac82036515a749bea5a55a64b43031a4.html "Specify the location in your LOAD TABLE statement to load data into data lake Relational Engine from data lake Files.") :arrow_upper_right:

[INSERT Statement for Data Lake Relational Engine](insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[LOAD\_ZEROLENGTH\_ASNULL Option for Data Lake Relational Engine](../090-database-options/load-zerolength-asnull-option-for-data-lake-relational-engine-a63c423.md "Specifies LOAD statement behavior under certain conditions.")

[NON\_ANSI\_NULL\_VARCHAR Option for Data Lake Relational Engine](../090-database-options/non-ansi-null-varchar-option-for-data-lake-relational-engine-a643a35.md "Controls whether zero-length VARCHAR data is treated as NULLs for insert, load, and update operations.")

[TEMP\_EXTRACT\_LENGTH\_PREFIX Option for Data Lake Relational Engine](../090-database-options/temp-extract-length-prefix-option-for-data-lake-relational-engine-1126138.md "Adds a prefix field of specified length (byte) for a varchar or varbinary column in the generated output file. This PREFIX field in the extract file holds the length of the column data.")

[TEMP\_EXTRACT\_VARYING Option for Data Lake Relational Engine](../090-database-options/temp-extract-varying-option-for-data-lake-relational-engine-ceb244e.md "Used in conjunction with TEMP_EXTRACT_LENGTH_PREFIX, the TEMP_EXTRACT_VARYING option outputs varchar or varbinary column data in a variable-length format in the extracted file. The prefix field specified by TEMP_EXTRACT_LENGTH_PREFIX option holds the length of column data.")

[Loading Parquet Files](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_1_QRC/en-US/a054ac0ce09e47799e5f24860378056b.html "Parquet is an efficient, open-source, column-oriented format file designed for Apache Hadoop. You can load tables in Parquet format using the data lake Relational Engine LOAD TABLE statement.") :arrow_upper_right:

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[SAP HANA Cloud, Data Lake Terminology](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_1_QRC/en-US/d003004765fb4475b14d83e5c51b117f.html "Definitions of data lake terms used in this document.") :arrow_upper_right:
