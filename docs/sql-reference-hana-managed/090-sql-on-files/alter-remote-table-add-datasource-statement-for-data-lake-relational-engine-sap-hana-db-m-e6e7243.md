<!-- loioe6e7243b09c34d48adf387e96f43c014 -->

# ALTER \(Remote\) TABLE ADD DATASOURCE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]

Attach an external data source, such as a file or directory, to a SQL on Files remote table.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioe6e7243b09c34d48adf387e96f43c014__section_inj_b3b_nqb"/>

## Usage

-   This topic is limited to SQL on Files use cases.

-   This data lake Relational Engine \(SAP HANA DB-Managed\) SQL on Files SQL statement can be used as follows:

    -   Connected to SAP HANA database as a SAP HANA database user..
    -   Using the REMOTE\_EXECUTE procedure. See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](../030-sql-statements/remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).





## Syntax

```
ALTER TABLE <remote-schema-name>.<remote-table-name> IN FILES_SERVICE ADD DATASOURCE
	[ AS <identifier> ]
	[ ( <datasource-column-spec>[, <datasource-column-spec>...] ) ]
		<datasource-file-format> ( <datasource-resource> ) 
		<datasource-encoding-clause>
	[ <datasource-option> ]


<datasource-column-spec> ::= 
	<column-name> 
		[ <datasource-column-from-clause> ]
		[ <datasource-column-default-clause> ]
		[ <datasource-column-option-list> ]

<datasource-column-from-clause> ::=  
	{ FROM COLUMN $<integer>
	 | FROM COLUMN <string-literal>
	 | FROM DIRECTORY $<integer>
	 | FROM VALUE <literal>
	 | FROM VALUE NULL }

<datasource-column-default-clause> ::=
	{ DEFAULT VALUE <string-literal> 
	 | DEFAULT VALUE <literal> 
	 | DEFAULT VALUE NULL }

<datasource-column-option-list> ::=
	<datasource-column-option>[ <datasource-column-option> ...]

<datasource-column-option> ::=
	<csv-format-option>

<csv-format-option> ::=
	{ STRING DELIMITED BY <string>
	 | DELIMITED BY <string>
	 | ESCAPE CHAR <string>
	 | DECIMAL SEPARATED BY <string>
	 | THOUSANDS SEPARATED BY <string>
	 | NULL <string>
	 | DATE <string>
	 | DATE ( <string> ) }

<datasource-file-format> ::= 
	{ PARQUET | ORC | CSV }

<datasource-resource> ::=
	{ ZIP ( <datasource-resource-string> )
	  <datasource-resource-string> }

<datasource-encoding-clause> ::=
	ENCODING { UTF_8 | CESU_8 | ISO_8859_1 }

<datasource-option-list> ::=
	<datasource-option>[ <datasource-option> ...]

<datasource-option> ::=
	{ <csv-format-option>
	 SKIP <integer> };
```



## Parameters


<dl>
<dt><b>

*<remote-schema-name\>*

</b></dt>
<dd>

The schema of the table. If a schema name is not provided, the datasource is added to the current schema.



</dd><dt><b>

*<remote-table-name\>*

</b></dt>
<dd>

The name of the table to be altered.



</dd><dt><b>

AS clause

</b></dt>
<dd>

Optional datasource name. You can reference the datasource by its name, otherwise a unique name is generated.



</dd><dt><b>

*<datasource-column-from-clause\>*

</b></dt>
<dd>

> ### Note:  
> If there is no FROM clause for a column, it is mapped by `FROM COLUMN $X`, where X is the zero based position of the column in the table, according to the CREATE TABLE statement.



</dd>
<dd>


<dl>
<dt><b>

<code> FROM COLUMN $ <i class="varname"> &lt;integer&gt; </i> </code>

</b></dt>
<dd>

Reads the column from the column in the file specified by a 0-based index. This can be used to skip columns during read.



</dd><dt><b>

<code> FROM COLUMN <i class="varname"> &lt;string-literal&gt; </i> </code>

</b></dt>
<dd>

Reads the column from a named column in the file. The name given by the *<string-literal\>* is case sensitive.



</dd><dt><b>

<code> FROM DIRECTORY $ <i class="varname"> &lt;integer&gt; </i> </code>

</b></dt>
<dd>

Reads the column from a directory name by extracting the value from the path segment starting from the location pointed to in *<datasource-resource-string\>*.

The value extraction from a path segments happens in the following steps:

1.  The segment is identified by splitting at `/`. `$0` refers to the first segment after a root path, increasing by one for every consecutive segment. The filename can not be used as a segment. If the segment is not found, querying the table will fail.
2.  If at least one '`=`' is found as part of the segment string, the substring after the first '`=`' is considered for further parsing. if no '`=`' is present, the full segment string is considered.
3.  The resulting byte sequence is parsed into the target type of the column.

Note that using a DATE, TIME, or TIMESTAMP format cannot be configured for `FROM DIRECTORY` mapped columns. The default values always apply.

See [Structuring a Data Lake Files Folder Hierarchy for Big Data](https://help.sap.com/viewer/3ef213750ce94aac885ac4fc54ea212f/2024_1_QRC/en-US/c712a4dff1ad429cad9a2a3e42336e42.html "Structure data for optimal performance by understanding how SQL on Files tables handle predicates.") :arrow_upper_right: for further examples and guidance on how to use `FROM DIRECTORY` mapping effectively.



</dd><dt><b>

<code> FROM VALUE <i class="varname"> &lt;literal&gt; </i> </code>

</b></dt>
<dd>

Fills the table column with a fixed value instead of reading it from source files.

CSV format options do not apply to the provided *<literal\>*. For example, `FROM VALUE '20-10-2011' DATE 'DD-MM-YYYY'` does not add a constant date. Instead, use `FROM VALUE '2011-10-20'`.

> ### Note:  
> In SAP HANA Database Explorer, the value for `fixedValue` is shown using its internal representation, not as the *<literal\>* text entered in the SQL statement.



</dd><dt><b>

`FROM VALUE NULL`

</b></dt>
<dd>

Fills the table column with the fixed value `NULL` instead of reading it from source files. `FROM VALUE NULL` is similar to <code>FROM VALUE <i class="varname">&lt;literal&gt;</i></code> where *<literal\>* is the NULL value.



</dd>
</dl>



</dd><dt><b>

*<datasource-column-default-clause\>*

</b></dt>
<dd>

Fills the table column with the default value if the column is missing in the datasource file.



</dd>
<dd>


<dl>
<dt><b>

<code> DEFAULT VALUE <i class="varname"> &lt;string-literal&gt; </i> </code>

</b></dt>
<dd>

Fills the table column with the fixed value specified in *<string-literal\>*.



</dd><dt><b>

DEFAULT VALUE *<literal\>*

</b></dt>
<dd>

Fills the table column with the fixed value specified in *<literal\>*.



</dd><dt><b>

DEFAULT VALUE NULL

</b></dt>
<dd>

Fills the table column with the NULL value.



</dd>
</dl>



</dd><dt><b>

*<datasource-column-option-list\>*

</b></dt>
<dd>

CSV format options. Options specified in *<datasource-column-option-list\>* apply for the current column and overwrite any options provided for the *<datasource-option\>* clause. For example, if an option is not specified in *<datasource-column-option-list\>*, the option in *<datasource-option\>* is used instead. These options only apply for CSV datasources and are silently ignored when specified for another file format.



</dd><dt><b>

*<datasource-file-format\>*

</b></dt>
<dd>

The file format to load from. The supported values are PARQUET, ORC, and CSV.



</dd><dt><b>

*<datasource-resource\>*

</b></dt>
<dd>


<dl>
<dt><b>

`ZIP`

</b></dt>
<dd>

Decompress the file before further processing. Supported compression methods are ZIP and GZIP. Only single compressed files are allowed; compressed directories and archives are not supported. `ZIP` works with CSV, PARQUET, and ORC formats.

If the *<datasource-resource-string\>* points to a directory, all files found in the folder hierarchy are assumed to be ZIP or GZIP files, unzipped individually, and then treated according to the file format.



</dd><dt><b>

*<datasource-resource-string\>*

</b></dt>
<dd>

SQL on Files supports strings following the `hdlfs:///path/to/root` format.

For example, the path for a file could be `hdlfs:///ORDER_CSV1000/0.data.csv`. For a directory or folder, either `hdlfs:///ORDER_CSV1000` or `hdlfs:///ORDER_CSV1000/` is supported, regardless of the inclusion of a trailing slash \( / \).

SQL on Files also supports filters in file names, which are shell wildcard patterns. The wildcard syntax follows glob patterns.

For example, filter all files with the ending `.csv` under a given path using the datasource string `hdlfs:///path/to/root/*.csv`. This returns `/path/to/root/file1.csv`, but not files under the `a` subfolder like `/path/to/root/a/file2.csv`. To also retrieve files under subfolders, use a globstar pattern, which performs a recursive search. To retrieve all files with the ending `.csv` under a given path and subfolders, use the datasource string `hdlfs:///path/to/root/**/*.csv`. This will return the files `/path/to/root/file1.csv` and `/path/to/root/a/file2.csv`.



</dd>
</dl>



</dd><dt><b>

`ENCODING`

</b></dt>
<dd>

Specifies the encoding of the files in this datasource. Supported encodings are UTF\_8, CESU\_8, and ISO\_8859\_1. These values **must** be entered in uppercase only. Data is internally converted to CESU\_8. If that conversion fails, a conversion error is returned. The encoding applies to all files in the datasource. Different datasources may have different encodings.



</dd><dt><b>

*<csv-format-option\>*

</b></dt>
<dd>

CSV format options can be specified for the column or for the whole CSV datasource. If a CSV option is specified for both a column and the datasource, the column setting takes precedence.


<dl>
<dt><b>

`STRING DELIMITED BY`

</b></dt>
<dd>

Identifies the enclosure character to place around string values, for TEXT data only. The delimiter is a single character, which can be an ASCII character or the hexadecimal character representation. The default is '`"`'. Using the same delimiter for both strings and columns is not allowed.



</dd><dt><b>

`DELIMITED BY`

</b></dt>
<dd>

The delimiter between columns of the file. The delimiter is a single character, which can be an ASCII character or the hexadecimal character representation. The default is '`|`'. For example, `a|b|c` represents 3 columns. DELIMITED BY can be specified only as a datasource option, not for a column.



</dd><dt><b>

`ESCAPE CHAR`

</b></dt>
<dd>

Specifies the escape character. The escape character is a single character, which can be an ASCII character or the hexadecimal character representation. If not specified, the default is '`"`'.



</dd><dt><b>

`DECIMAL SEPARATED BY`

</b></dt>
<dd>

The decimal separator is a single character, which can be an ASCII character or the hexadecimal character representation. The default is '`.`'.



</dd><dt><b>

`THOUSANDS SEPARATED BY`

</b></dt>
<dd>

The thousands separator is a single character, which can be an ASCII character or the hexadecimal character representation, or an empty string. The default is the empty string ' '.



</dd><dt><b>

`NULL`

</b></dt>
<dd>

By default, values with '`?`' are considered to be NULL. You can change this to any other string, like 'nil' or 'NULL'.



</dd><dt><b>

`DATE`

</b></dt>
<dd>

Specifies the format of `DATE`, `TIME`, and `TIMESTAMP` columns in CSV files.

The default for `DATE` columns is `YYYY-MM-DD`. The default for `TIME` columns is `HH24:MI:SF`. The default for `TIMESTAMP` columns is `YYYY-MM-DD HH24:MI:SF`.

> ### Note:  
> Providing a `DATE` format at the datasource level specifies the format for all `DATE`, `TIME`, and `TIMESTAMP` columns. Use the `DATE` format specifier at the column level for more control.

The following format specifiers are available for SQL on Files tables:


<table>
<tr>
<th valign="top">

Format Specifier

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`YYYY` 

</td>
<td valign="top">

The year, including the century. Range = \[0001,9999\]. The default is 1.

</td>
</tr>
<tr>
<td valign="top">

`RRRR` 

</td>
<td valign="top">

The year, with or without the century. Range = \[0001,9999\] or \[00,99\]. The default is 1.

If the century is provided, the behavior is the same as for `YYYY`.

If the century is not provided, the following is returned:

-   The specified two-digit year is 00 to 49:

    -   If the last two digits of the current year are 00 to 49, then the returned year has the same century as the current year.

    -   If the last two digits of the current year are 50 to 99, then the century of the returned year is 1 greater than the century of the current year.


-   The specified two-digit year is 50 to 99:

    -   If the last two digits of the current year are 00 to 49, then the century of the returned year is 1 less than the century of the current year.

    -   If the last two digits of the current year are 50 to 99, then the returned year has the same century as the current year.





</td>
</tr>
<tr>
<td valign="top">

`RR` 

</td>
<td valign="top">

The year, without the century. Range = \[00,99\]. The same behavior occurs as for `RRRR` when the century is omitted. The default is 1.

</td>
</tr>
<tr>
<td valign="top">

`MM` 

</td>
<td valign="top">

A numerical month value. Range = \[01,12\]. The default is 1.

</td>
</tr>
<tr>
<td valign="top">

`MON` 

</td>
<td valign="top">

An abbreviated month name \(for example, DEC\).

</td>
</tr>
<tr>
<td valign="top">

`MONTH` 

</td>
<td valign="top">

The full month name \(for example, DECEMBER\).

</td>
</tr>
<tr>
<td valign="top">

`DD` 

</td>
<td valign="top">

The day of the month. Range = \[01,31\]. The default is 1.

</td>
</tr>
<tr>
<td valign="top">

`DDD` 

</td>
<td valign="top">

A numerical value representing a day of the year. Range = \[001,366\]. The default is 1.

</td>
</tr>
<tr>
<td valign="top">

`HH` 

</td>
<td valign="top">

The hour, in 12 or 24 hour format, depending on if `AP` is included. Range = \[00,23\] or \[01,12\]. The default is 0.

</td>
</tr>
<tr>
<td valign="top">

`HH12` 

</td>
<td valign="top">

The hour, in 12 hour format. Range = \[01,12\]. `AP` is required. The default is 0.

</td>
</tr>
<tr>
<td valign="top">

`HH24` 

</td>
<td valign="top">

The hour, in 24 hour format. Range = \[00,23\]. The default is 0.

</td>
</tr>
<tr>
<td valign="top">

`AP` 

</td>
<td valign="top">

Meridian indicator. Range = \{AM,PM\}.

</td>
</tr>
<tr>
<td valign="top">

`MI` 

</td>
<td valign="top">

The minute of the hour. Range = \[00,59\]. The default is 0.

</td>
</tr>
<tr>
<td valign="top">

`SS` 

</td>
<td valign="top">

The second of the minute. Range = \[00,59\]. The default is 0.

</td>
</tr>
<tr>
<td valign="top">

`SSSSS` 

</td>
<td valign="top">

The second of the day. Range = \[00,86399\]. The default is 0.

</td>
</tr>
<tr>
<td valign="top">

`SF` 

</td>
<td valign="top">

The second of the minute, with an optional fraction separated by a period \( . \).

</td>
</tr>
<tr>
<td valign="top">

`FF[1-7]` 

</td>
<td valign="top">

The fraction of a second, in 100 nanoseconds. Range = \[0000000,9999999\]. The default is 0.

The precision specifier is optional; the default is 7. Leading zeros are recognized \(for example, 0010000 yields 1 millisecond\).

</td>
</tr>
</table>

> ### Restriction:  
> -   Only one month specifier can occur in a format.
> 
> -   `DDD` can't occur together with `DD` or any other month specifier.
> 
> -   Only one hour specifier can occur in a format.
> 
> -   If `HH24` occurs, `AP` must not occur as well. If `HH12` occurs, `AP` needs to occur as well.
> 
> -   `SSSSS` cannot occur together with `MI` or any hour specifier.
> 
> -   The given date expression must match the given format. Trailing spaces are ignored if the expression is of type CHAR and either the format is omitted or is also of type CHAR.
> 
> -   The number of digits in a numeric field can't exceed the length of the format specifier.
> 
> -   The given date, time, and timestamp expressions must be valid.



</dd>
</dl>



</dd><dt><b>

*<datasource-option\>*

</b></dt>
<dd>

Specifies the *<csv-format-option\>* for CSV datasources and the SKIP clause.


<dl>
<dt><b>

`SKIP`

</b></dt>
<dd>

The number of lines at the beginning of each file to skip, for example, headers. The default is 0 \(no skip\).



</dd>
</dl>



</dd>
</dl>



<a name="loioe6e7243b09c34d48adf387e96f43c014__section_pkw_2fb_nqb"/>

## Privileges

To use REMOTE\_EXECUTE requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loioe6e7243b09c34d48adf387e96f43c014__section_dg3_gxp_wqb"/>

## Examples

The following examples use the following table:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE(
  'CREATE TABLE external_schema.external_table(
  keyColumn BIGINT,
  name VARCHAR(80),
  category SMALLINT,
  extraInfo VARCHAR(120)
 )IN FILES_SERVICE'
);
```



### Example 1

The following example adds a datasource, omitting all default parameters:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE(
  'ALTER TABLE external_schema.external_table IN FILES_SERVICE ADD DATASOURCE
  CSV(''hdlfs:///marketing/joe/2021/'') ENCODING ''UTF_8'''
);
```



### Example 2

The following example adds a file as a datasource:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE(
  'ALTER TABLE external_schema.external_table IN FILES_SERVICE ADD DATASOURCE
	(category FROM DIRECTORY $0, extraInfo FROM COLUMN $2)
	CSV(''hdlfs:///marketing/joe/q4_2021.csv'') ENCODING ''UTF_8'''
);
```



### Example 3

The following example uses a Parquet file format and identifies two columns:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE(
  'ALTER TABLE external_schema.external_table IN FILES_SERVICE ADD DATASOURCE AS ds_name_2
  (keyColumn FROM COLUMN ''key_col'', category FROM COLUMN ''cat'')
  PARQUET(''hdlfs:///marketing/amy/2020/'') ENCODING ''UTF_8'''
);
```



### Example 4

The following example adds a directory as a datasource, where all files in `q1_2022` with a supported extension will be used:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE(
  'ALTER TABLE external_schema.external_table IN FILES_SERVICE ADD DATASOURCE
	(category FROM DIRECTORY $0, extraInfo FROM COLUMN $2)
	CSV(''hdlfs:///marketing/joe/q1_2022/'') ENCODING ''UTF_8'''
);
```

**Related Information**  


[REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](../030-sql-statements/remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md "To run data lake Relational Engine SQL statements using the SAP HANA database REMOTE_EXECUTE or REMOTE_EXECUTE_DDL procedure, you embed the SQL syntax within the procedure.")

[ALTER \(Remote\) TABLE DROP DATASOURCE Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\) \[SQL on Files\]](alter-remote-table-drop-datasource-statement-for-data-lake-relational-engine-sap-hana-db-1e570af.md "Remove a data source from a SQL on Files table.")

[ALTER (Remote) TABLE ADD DATASOURCE Statement for Data Lake Relational Engine \[SQL on Files\]](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/65c9d8fb06914172a3960b804f7613f3.html "Attach an external data source, such as a file or directory, to a SQL on Files remote table.") :arrow_upper_right:

