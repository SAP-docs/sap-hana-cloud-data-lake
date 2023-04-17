<!-- loioa6215ada84f2101596dfe103bbef22a4 -->

# OPEN Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Opens a previously declared cursor to access information from the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
OPEN <cursor-name>
   ... [ USING [ DESCRIPTOR { <sqlda-name> | <host-variable> } [, …]  ] ]
   ... [ WITH HOLD ]
```



<a name="loioa6215ada84f2101596dfe103bbef22a4__IQ_Parameters"/>

## Parameters

 *<cursor-name\>*
 :   Identifier or host-variable.

    If the cursor name is specified by an identifier or string, then the corresponding `DECLARE CURSOR` statement must appear prior to the `OPEN` in the C program; if the cursor name is specified by a host variable, then the `DECLARE CURSOR` statement must execute before the `OPEN` statement.

  USING
 :   Specifies the host variables that are bound to the placeholder bind variables in the `SELECT` statement for which the cursor has been declared.

  *<sqlda-name\>*
 :   Identifier

  WITH HOLD
 :   Keeps the cursor open for subsequent transactions. The cursor remains open until the end of the current connection or until an explicit `CLOSE` statement is executed. Cursors are automatically closed when a connection is terminated.

 

<a name="loioa6215ada84f2101596dfe103bbef22a4__IQ_Usage"/>

## Remarks

By default, all cursors are automatically closed at the end of the current transaction \(`COMMIT` or `ROLLBACK`\).

The cursor is positioned before the first row.

A cursor declared using the FOR READ ONLY clause sees the version of table\(s\) on which the cursor is declared when the cursor is opened, not the version of table\(s\) at the time of the first `FETCH` statement.

The USING DESCRIPTOR sqlda-name, `host-variable`, and BLOCK n clauses are for Embedded SQL only.

After successful execution of the `OPEN` statement, the sqlerrd\[3\] field of the SQLCA \(SQLIOESTIMATE\) is filled in with an estimate of the number of input/output operations required to fetch all rows of the query. Also, the sqlerrd\[2\] field of the SQLCA \(SQLCOUNT\) is filled in with either the actual number of rows in the cursor \(a value greater than or equal to 0\), or an estimate thereof \(a negative number whose absolute value is the estimate\). The sqlerrd\[2\] field is the actual number of rows, if the database server can compute this value without counting the rows.



<a name="loioa6215ada84f2101596dfe103bbef22a4__IQ_Permissions"/>

## Privileges

-   Must have SELECT object-level permission on all tables in a `SELECT` statement or EXECUTE object-level permission on the procedure in a `CALL` statement.
-   When the cursor is on a `CALL` statement, `OPEN` causes the procedure to execute until the first result set \(`SELECT` statement with no INTO clause\) is encountered. If the procedure completes and no result set is found, the SQLSTATE\_PROCEDURE\_COMPLETE warning is set.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa6215ada84f2101596dfe103bbef22a4__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products—The simple <code>OPEN <i class="varname">&lt;cursor-name&gt;</i></code> syntax is supported by SAP Adaptive Server Enterprise. None of the other clauses are supported in SAP ASE stored procedures. Open Client/Open Server supports the `USING` descriptor or host name variable syntax.



<a name="loioa6215ada84f2101596dfe103bbef22a4__IQ_Examples"/>

## Examples

-   The following example uses `OPEN` in Embedded SQL:

    ```
    EXEC SQL OPEN employee_cursor;
    ```

    and

    ```
    EXEC SQL PREPARE emp_stat FROM
    'SELECT EmployeeID, Surname FROM Employees WHERE name like ?';
    EXEC SQL DECLARE employee_cursor CURSOR FOR emp_stat;
    EXEC SQL OPEN employee_cursor USING :pattern;
    ```

-   The following example is from a procedure:

    ```
    BEGIN
    DECLARE cur_employee CURSOR FOR
      SELECT Surname
      FROM Employees ;
    DECLARE name CHAR(40) ;
    OPEN cur_employee;
    LOOP
    FETCH NEXT cur_employee into name ;
       ...
    END LOOP
    CLOSE cur_employee;
    END
    ```


**Related Information**  


[CLOSE Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](close-statement-esql-sp-for-data-lake-relational-engine-a6157e8.md "Closes a named cursor.")

[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[FETCH Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](fetch-statement-esql-sp-for-data-lake-relational-engine-a61e5e2.md "Retrieves one row from the named cursor. The cursor must have been previously opened.")

[PREPARE Statement \[ESQL\] for Data Lake Relational Engine](prepare-statement-esql-for-data-lake-relational-engine-a621eea.md "Prepares a statement to be executed later or used for a cursor.")

[RESUME Statement for Data Lake Relational Engine](resume-statement-for-data-lake-relational-engine-a6239b4.md "Resumes execution of a procedure that returns result sets.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

