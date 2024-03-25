<!-- loioa6239b4d84f2101594fce0499fe8dd88 -->

# RESUME Statement for Data Lake Relational Engine

Resumes execution of a procedure that returns result sets.



<a name="loioa6239b4d84f2101594fce0499fe8dd88__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1 – Supported in `dbisqlc`

</b></dt>
<dd>

```
RESUME <cursor-name>
```



</dd><dt><b>

Syntax 2 – Supported in `dbisql`

</b></dt>
<dd>

```
RESUME [ ALL ]
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6239b4d84f2101594fce0499fe8dd88__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<cursor-name\>*

</b></dt>
<dd>

Identifier or host-variable



</dd>
</dl>



<a name="loioa6239b4d84f2101594fce0499fe8dd88__IQ_Usage"/>

## Remarks

The procedure executes until the next result set \(`SELECT` statement with no INTO clause\) is encountered. If the procedure completes and no result set is found, the SQLSTATE\_PROCEDURE\_COMPLETE warning is set. This warning is also set when you `RESUME` a cursor for a `SELECT` statement.

Syntax 1 – supported in `dbisqlc` but not `dbisql` \(Interactive SQL\) or when connected to the database using the SAP SQL Anywhere

Syntax 2 – supported in `dbisql`. Resumes the current procedure. If ALL is not specified, executing JDBC driver.`RESUME` displays the next result set or, if no more result sets are returned, completes the procedure. In `dbisql`, the `RESUME ALL` statement cycles through all result sets in a procedure, without displaying them, and completes the procedure. This is useful mainly in testing procedures.

The cursor must have been previously opened.



<a name="loioa6239b4d84f2101594fce0499fe8dd88__IQ_Permissions"/>

## Privileges

None



<a name="loioa6239b4d84f2101594fce0499fe8dd88__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa6239b4d84f2101594fce0499fe8dd88__IQ_Examples"/>

## Examples

-   JDBCThe following example shows embedded SQL:

    ```
    EXEC SQL RESUME cur_employee;
    ```

    ```
    EXEC SQL RESUME :cursor_var;
    ```

-   The following example shows `dbisql`:

    ```
    CALL sample_proc() ;
    RESUME ALL;
    ```


**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

