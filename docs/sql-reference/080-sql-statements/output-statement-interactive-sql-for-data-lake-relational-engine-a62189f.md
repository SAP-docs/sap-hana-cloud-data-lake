<!-- loioa62189f884f21015aeec89ba6534af52 -->

# OUTPUT Statement \[Interactive SQL\] for Data Lake Relational Engine

Writes the information retrieved by the current query to a file.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
OUTPUT TO <filename> 
   [ APPEND ] [ VERBOSE ]
   [ FORMAT <output-format> ] 
   [ ESCAPE CHARACTER <character> ] 
   [ DELIMITED BY <string> ] 
   [ QUOTE <string> [ ALL ] ] 
   [ COLUMN WIDTHS ( <integer>, … ) ]
   [ HEXADECIMAL { ON | OFF | ASIS } ]
   [ ENCODING <encoding> ]
   [ WITH COLUMN NAMES ]
```

```
<output-format> ::=
   { TEXT | FIXED | HTML | SQL | XML }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa62189f884f21015aeec89ba6534af52__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

FORMAT

</b></dt>
<dd>

The output format. If no FORMAT clause is specified, the Interactive SQL `OUTPUT_FORMAT` database option setting is used.



</dd><dt><b>

TEXT

</b></dt>
<dd>

Output is a TEXT format file with one row per line in the file. All values are separated by commas, and strings are enclosed in apostrophes \(single quotes\). The delimiter and quote strings can be changed using the DELIMITED BY and QUOTE clauses. If the ALL clause is specified in the QUOTE clause, all values \(not just strings\) are quoted. TEXT is the default output format.

Three other special sequences are also used. The two characters `\n` represent a newline character, `\\` represents a single `\`, and the sequence `\xDD` represents the character with hexadecimal code DD.

If you are exporting Java methods that have string return values, you must use the HEXADECIMAL OFF clause.



</dd><dt><b>

FIXED

</b></dt>
<dd>

Output is fixed format with each column having a fixed width. The width for each column can be specified using the COLUMN WIDTHS clause. No column headings are output in this format.

If you omit the COLUMN WIDTHS clause, the width for each column is computed from the data type for the column, and is large enough to hold any value of that data type. The exception is that LONG VARCHAR and LONG BINARY data defaults to 32 KB.



</dd><dt><b>

HTML

</b></dt>
<dd>

Output is in the Hyper Text Markup Language format.



</dd><dt><b>

SQL

</b></dt>
<dd>

Output is an Interactive SQL `INPUT` statement required to re-create the information in the table.

> ### Note:  
> Data lake Relational Engine does not support the `INPUT` statement. Change this statement to a valid `LOAD TABLE` \(or `INSERT`\) statement to use it to load data back in.



</dd><dt><b>

XML

</b></dt>
<dd>

Output is an XML file encoded in UTF-8 and containing an embedded DTD. Binary values are encoded in CDATA blocks with the binary data rendered as 2-hex-digit strings. The `LOAD TABLE` statement does not accept XML as a file format.



</dd><dt><b>

APPEND

</b></dt>
<dd>

Appends the results of the query to the end of an existing output file without overwriting the previous contents of the file. By default, if you do not use APPEND clause, the `OUTPUT` statement overwrites the contents of the output file.

The APPEND clause is valid if the output format is TEXT, FIXED, or SQL.



</dd><dt><b>

VERBOSE

</b></dt>
<dd>

Error messages about the query, the SQL statement used to select the data, and the data itself are written to the output file. By default, if you omit the VERBOSE clause, only the data is written to the file. The VERBOSE clause is valid if the output format is TEXT, FIXED, or SQL.



</dd><dt><b>

ESCAPE CHARACTER

</b></dt>
<dd>

The default escape character for characters stored as hexadecimal codes and symbols is a backslash \(\\\), so \\x0A is the line feed character, for example.

To change this default, use the ESCAPE CHARACTER clause. For example, to use the exclamation mark as the escape character, enter:

```
... ESCAPE CHARACTER '!'
```



</dd><dt><b>

DELIMITED BY

</b></dt>
<dd>

For the TEXT output format only. The delimiter string, by default a comma, is placed between columns.



</dd><dt><b>

QUOTE

</b></dt>
<dd>

For the TEXT output format only. The quote string, by default a single quote character, is placed around string values. If ALL is specified in the QUOTE clause, the quote string is placed around all values, not just around strings.



</dd><dt><b>

COLUMN WIDTHS

</b></dt>
<dd>

Specifies column widths for the FIXED format output.



</dd><dt><b>

HEXADECIMAL

</b></dt>
<dd>

Specifies how binary data is to be unloaded for the TEXT format only. When set to ON, binary data is unloaded in the format 0xabcd. When set to OFF, binary data is escaped when unloaded \(\\xab\\xcd\). When set to ASIS, values are written without any escaping even if the value contains control characters. ASIS is useful for text that contains formatting characters such as tabs or carriage returns.



</dd><dt><b>

ENCODING

</b></dt>
<dd>

Specifies the encoding that is used to write the file. You can use the ENCODING clause only with the TEXT format. Can be a string or identifier.

If you do not specify the ENCODING clause, Interactive SQL determines the code page that is used to write the file as follows, where code page values occurring earlier in the list take precedence over those occurring later:

-   The code page specified with the `DEFAULT_ISQL_ENCODING` option \(if this option is set\)
-   The default code page for the computer Interactive SQL is running on



</dd>
</dl>



<a name="loioa62189f884f21015aeec89ba6534af52__IQ_Usage"/>

## Remarks

The current query is the `SELECT` or `LOAD TABLE` statement that generated the information that appears on the *Results* tab in the Results pane. The `OUTPUT` statement reports an error if there is no current query.

> ### Note:  
> `OUTPUT` is especially useful in making the results of a query or report available to another application, but is not recommended for bulk operations. For high-volume data movement, use the ASCII and BINARY data extraction functionality with the `SELECT` statement. The extraction functionality provides much better performance for large-scale data movement, and creates an output file you can use for loads.



<a name="loioa62189f884f21015aeec89ba6534af52__IQ_Permissions"/>

## Privileges

None



<a name="loioa62189f884f21015aeec89ba6534af52__IQ_Side_Effects"/>

## Side Effects

In Interactive SQL, the *Results* tab displays only the results of the current query. All previous query results are replaced with the current query results.



<a name="loioa62189f884f21015aeec89ba6534af52__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not applicable



<a name="loioa62189f884f21015aeec89ba6534af52__IQ_Examples"/>

## Examples

-   The following example places the contents of the `Employees` table in a text file:

    ```
    SELECT * FROM Employees; 
    OUTPUT TO employees.txt FORMAT TEXT
    ```

-   The following example places the contents of the `Employees` table at the end of an existing file, and includes any messages about the query in this file as well:

    ```
    SELECT * FROM Employees; 
    OUTPUT TO employees.txt APPEND VERBOSE
    ```

-   The following example exports a value that contains an embedded line feed character. A line feed character has the numeric value 10, which you can represent as the string '`\x0a`' in a SQL statement.

    Execute this statement with HEXADECIMAL ON:

    ```
    SELECT 'line1\x0aline2'; OUTPUT TO file.txt HEXADECIMAL ON
    ```

    The result is a file with one line in it, containing this text:

    ```
    line10x0aline2
    ```

    Execute the same statement with HEXADECIMAL OFF:

    ```
    line1\x0aline2
    ```

    If you set `HEXADECIMAL` to ASIS, the result is a file with two lines:

    ```
    'line1
    line2'
    ```

    Using ASIS generates two lines, because the embedded line feed character has been exported without being converted to a two-digit hex representation, and without a prefix.


**Related Information**  


[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

[DEFAULT\_ISQL\_ENCODING Option \[Interactive SQL\] for Data Lake Relational Engine](../090-database-options/default-isql-encoding-option-interactive-sql-for-data-lake-relational-engine-a63407d.md "Specifies the code page used by READ and OUTPUT statements.")

