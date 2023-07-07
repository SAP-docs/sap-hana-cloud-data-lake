<!-- loioe048737551b84b2a8b66258adab4a9b3 -->

# LOAD TABLE Statement for Data Lake Relational Engine \(Parquet Format\)

Imports data from Parquet files into a data lake Relational Engine database table from either an external object store \(Azure BLOB storage, an Amazon S3 bucket, S3-compliant bucket, or Google Cloud Storage\) or from data lake Files containers \(the managed object store\).



For information on loading data in other formats, see [LOAD TABLE Statement for Data Lake Relational Engine \(Non-Parquet Formats\)](load-table-statement-for-data-lake-relational-engine-non-parquet-formats-7ca3f60.md).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
LOAD [ INTO ] TABLE [ { <owner> | <schema-name> }.]<table-name>
    { <object-store-sources> | <client-file-sources> | <parquet-load-group>[, ...] }
    [ CONNECTION_STRING <connection-string> ]
    [ CHECK CONSTRAINTS { ON | OFF } ]
    [ DEFAULTS { ON | OFF } ]
    ESCAPES OFF
    FORMAT PARQUET
    [ STRIP { OFF | RTRIM } ]
    [ LIMIT <number-of-rows> ]
    [ NOTIFY <number-of-rows> ]
    [ ON FILE ERROR { ROLLBACK | FINISH | CONTINUE } ]
    [ PREVIEW { ON | OFF } ] 
    [ WORD SKIP <number> ]
    [ IGNORE CONSTRAINT <constraint-type> <string> ]
    [ MESSAGE LOG '<string>' ]
    [ ROW LOG '<string>' ]
    [ ONLY LOG <log-what> [, …] ]
    [ LOG DELIMITED BY [, …] ]
    [ ALLOW MISSING COLUMNS { ON | OFF } ]
    [ WITH MATCHING COLUMN NAMES ]

<parquet-load-group> ::= '(' <load-column> [, ...] ')' { <object-store-sources> | <client-file-sources> }

<object-store-sources> ::= { FROM | USING FILE } <single-object-store-sources>[, ...]

<single-object-store-source> ::= { '<filename-string>' | <filename-variable> } [ WITH ETAG '<etag>' ]

<client-file-sources> ::= USING CLIENT FILE { '<filename-string>' | <filename-variable> }[, ...]

<load-column> ::=
          <column-name> [ <parquet-from-column> ] [ <column-spec> ] [ <nulls-spec> ]
        | FILLER()
        | <column-name> VALUE <default-value>

<parquet-from-column> ::=
        FROM COLUMN { '<parquet-column-name>' | <parquet-column-position> } [ MISSING DEFAULT <default-value> ]
        | MISSING DEFAULT <default-value> 

<column-spec> ::= 
   DATE ( <input-date-format> )
   | DATETIME ( <input-datetime-format> )
   | { BINARY | ASCII } FILE ( <integer> )
   | { BINARY | ASCII } FILE ( '<string>' )
   | FILE NAME
   | FILE ETAG

<nulls-spec> ::= NULL ( { BLANKS | ZEROS | '<literal>' } [, ...] )

constraint-type string ::=
   { CHECK limit
   | UNIQUE limit
   | NULL limit
   | FOREIGN KEY limit [, ...]
   | DATA VALUE limit
   | ALL limit }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioe048737551b84b2a8b66258adab4a9b3__load_table_parameters1_parquetformat"/>

## Parameters



### \{FROM | USING | USING CLIENT \} FILE


<dl>
<dt><b>



</b></dt>
<dd>

> ### Note:  
> The FROM and USING clauses are synonymous.


<dl>
<dt><b>

Files Stored in data lake Files

</b></dt>
<dd>

The data source referenced by the filename is in the default data lake Files container.

The prefix `hdlfs:` identifies the file path as a data lake Files data source.

This example loads from a CSV file:

```
LOAD TABLE t1(c1) FROM 'hdlfs:///employeelist.csv'
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

Since *<filename-string\>* is passed to the server as a string, it's subject to the same formatting requirements as other SQL strings.

To specify more than one object, use a comma to separate each *<filename-string\>*.

If *<filename-string\>* WITH ETAG '<etag\>' is specified, the named object is loaded only if the ETag value matches. If a list of objects is specified and some of the ETags do not match, the LOAD statement will treat unmatched ETags as a file error and take the action specified by the ON FILE ERROR \{ ROLLBACK | FINISH | CONTINUE \} option. It will also be treated as a file error if the ETtag of an object changes while it is being loaded.

Because of resource constraints, data lake Relational Engine doesn't guarantee that all the data can be loaded. If resource allocation fails, the entire load transaction is rolled back.

USING CLIENT FILE bulk loads one or more files from a client. Client-side bulk loading only supports single threaded processing for each file

When bulk loading external BLOBs \(using *<column-spec\>* FILE NAME\), the USING CLIENT FILE clause applies to both primary and secondary files.

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

Specifies connection information

```
<connection-string> ::= 
   { <azure-connection> 
   | <s3-connection>  
   | <google-connection>}
```


<dl>
<dt><b>

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



### CHECK CONSTRAINTS \{ ON | OFF \}


<dl>
<dt><b>



</b></dt>
<dd>

Evaluates check constraints, which you can ignore or log. CHECK CONSTRAINTS defaults to ON.

Setting CHECK CONSTRAINTS OFF causes data lake Relational Engine to ignore all check constraint violations. This can be useful, for example, during database rebuilding. If a table has check constraints that call user-defined functions that are not yet created, the rebuild fails unless this clause is set to OFF.

This clause is mutually exclusive to the following clauses. If any of these options are specified in the same load, an error results:

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



### ESCAPES


<dl>
<dt><b>



</b></dt>
<dd>

For data lake Relational Engine, you need to set ESCAPES OFF.



</dd>
</dl>



### FORMAT parquet


<dl>
<dt><b>



</b></dt>
<dd>

Specify `.parquet` or `.parq` as the file name extension.

See [Loading Parquet Files](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_2_QRC/en-US/a054ac0ce09e47799e5f24860378056b.html "Parquet is an efficient, open-source, column-oriented format file designed for Apache Hadoop. You can load tables in Parquet format using the data lake Relational Engine LOAD TABLE statement.") :arrow_upper_right: in *SAP HANA Cloud, Data Lake Load and Unload Management* for more information.



</dd>
</dl>



### STRIP \{ OFF | RTRIM\}


<dl>
<dt><b>



</b></dt>
<dd>

Determines whether values should have trailing blanks stripped off before they are inserted. These STRIP keywords are accepted:

-   STRIP OFF – does not strip off trailing blanks
-   STRIP RTRIM – strips trailing blanks.
-   \(Deprecated\) STRIP ON – is deprecated. Use STRIP RTRIM.

With STRIP turned on \(the default\), data lake Relational Engine strips trailing blanks from values before inserting them. This is effective only for VARCHAR data. STRIP OFF preserves trailing blanks.



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

Specifies that you be notified with a message each time the specified number of rows is successfully inserted into the table. The default is 0, meaning no notifications are printed. The value of this clause overrides the value of the NOTIFY\_MODULUS database option.



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

Various combinations of the IGNORE CONSTRAINT and MESSAGE LOG options result in different logging actions:


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
> Set the IGNORE CONSTRAINT option limit to a nonzero value, if you are logging the ignored integrity constraint violations. If a single row has more than one integrity constraint violation, a row for each violation is written to the MESSAGE LOG file. Logging an excessive number of violations affects the performance of the load.



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



### WITH MATCHING COLUMN NAMES


<dl>
<dt><b>



</b></dt>
<dd>

Specifies that the column names in the data lake Relational Engine table match the column names in the Parquet files being loaded. This is equivalent to specifying FROM COLUMN '*<iq-column-name\>*' for each column in the load specification. For example, the following two statements are equivalent:

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



</dd>
</dl>



<a name="loioe048737551b84b2a8b66258adab4a9b3__load_table_remarks1_parquet"/>

## Remarks

The LOAD TABLE statement allows efficient mass insertion into a database table from multiple file types. Its clauses also let you control load behavior when integrity constraints are violated and to log information about the violations.

You can use LOAD TABLE on a temporary table, but the temporary table must have been declared with ON COMMIT PRESERVE ROWS or the next COMMIT removes the rows you've loaded.

LOAD TABLE supports loading of large object \(LOB\) data.



### Error Messages

-   If the specified load format isn't PARQUET, data lake Relational Engine returns the message “***Only ASCII, BCP, BINARY, PARQUET, and CSV are supported LOAD formats.***”
-   If the load default value specified is AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT, data lake Relational Engine returns the error “***Default value %2 cannot be used as a LOAD default value. %1***”
-   If the LOAD TABLE specification doesn't contain any columns that need to be loaded from the file specified, data lake Relational Engine returns the error “***The LOAD statement must contain at least one column to be loaded from input file.***” and the LOAD TABLE statement rolls back.
-   If a load exceeds the limit on the maximum number of terms for a text document with TEXT indexes, data lake Relational Engine returns the error “***Text document exceeds maximum number of terms. Support up to 4294967295 terms per document.***”



### Column Options

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


The NULL portion of the *<column-spec\>* indicates how to treat certain input values as NULL values when loading into the table column. These characters can include BLANKS, ZEROS, or any other list of literals you define. When specifying a NULL value or reading a NULL value from the source file, the destination column must be able to contain NULLs.

ZEROS are interpreted as follows: the cell is set to NULL if \(and only if\) the input data \(before conversion, if ASCII\) is all binary zeros \(and not character zeros\).

-   If the input data is character zero, then:

    1.  NULL \(ZEROS\) never causes the cell to be NULL.
    2.  NULL \('0'\) causes the cell to be NULL.

-   If the input data is binary zero \(all bits clear\), then:

    1.  NULL \(ZEROS\) causes the cell to be NULL.
    2.  NULL \('0'\) never causes the cell to be NULL.


If the length of a VARCHAR cell is zero and the cell is NULL, you get a zero-length cell. For all other data types, if the length of the cell is zero, data lake Relational Engine inserts a NULL. This is ANSI behavior. For non-ANSI treatment of zero-length character data, set the NON\_ANSI\_NULL\_VARCHAR database option.

Use the VALUE clause to specify a load default column value. You can load a default value into a column, even if the column doesn't have a default value defined in the table schema. This feature provides more flexibility at load time.

-   The LOAD TABLE DEFAULTS clause must be ON in order to use the default value specified in the LOAD TABLE statement. If the DEFAULTS clause is OFF, the specified load default value is used and a NULL value is inserted into the column instead.
-   The LOAD TABLE statement must contain at least one column that needs to be loaded from the file specified in the LOAD TABLE statement. Otherwise, an error is reported and the load is performed.
-   The specified load default value must conform to the supported default values for columns and default value restrictions. The LOAD TABLE DEFAULT clause doesn't support AUTOINCREMENT, IDENTITY, or GLOBAL AUTOINCREMENT as a load default value.
-   Encryption of the default value isn't supported for the load default values specified in the VALUE clause.
-   A constraint violation caused by evaluation of the specified load default value is counted for each row that is inserted in the table.

Use the MISSING DEFAULT option to specify a default column value to use if the column cannot be matched with a column in the loaded file. This option only applies when ALLOW MISSING COLUMNS is ON.



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



<a name="loioe048737551b84b2a8b66258adab4a9b3__IQ_Permissions"/>

## Privileges

To load tables and views requires one of:

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



<a name="loioe048737551b84b2a8b66258adab4a9b3__load_table_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioe048737551b84b2a8b66258adab4a9b3__load_table_examples1_parquet"/>

## Examples

**Example 1:** This example loads a Parquet file. The statement loads five columns into table T6 from Parquet file `MULTI.PARQUET`.

Example 1 syntax for Azure:

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

Example 1 syntax for Amazon S3:

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

Example 1 syntax for SAP Converged Cloud, which is an S3-compliant provider:

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

\(DEPRECATED\) Example 1 syntax for Amazon S3:

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

Example 1 syntax for Google Cloud:

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

Example 2 syntax showing LOAD from data lake Files:

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

This example ignores 10 word-length violations; on the 11th, it deploys the new error and rolls back the load:

```
LOAD TABLE PTAB1(
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


[Loading Parquet Files](https://help.sap.com/viewer/a8942f1c84f2101594aad09c82c80aea/2023_2_QRC/en-US/a054ac0ce09e47799e5f24860378056b.html "Parquet is an efficient, open-source, column-oriented format file designed for Apache Hadoop. You can load tables in Parquet format using the data lake Relational Engine LOAD TABLE statement.") :arrow_upper_right:

