<!-- loioa774406384f21015b6b5b37c393396c9 -->

# EXECUTE Statement \[ESQL\] for Data Lake Relational Engine

Executes a SQL statement.



<a name="loioa774406384f21015b6b5b37c393396c9__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1 – Executes a Previously Prepared Named Dynamic Statement

</b></dt>
<dd>

```
EXECUTE <statement-name>
   ... [ { USING DESCRIPTOR <sqlda-name> | USING <host-variable-list> } ]
   ... [ { INTO DESCRIPTOR <into-sqlda-name> | INTO <into-host-variable-list> } ]
   ... [ ARRAY :<nnn> ];
```



</dd><dt><b>

Syntax 2 – Short Form to PREPARE and EXECUTE a Statement Not Containing Bind Variables or Output

</b></dt>
<dd>

```
EXECUTE IMMEDIATE <statement>;
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa774406384f21015b6b5b37c393396c9__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<statement-name\>*

</b></dt>
<dd>

Identifier or host-variable.



</dd><dt><b>

*<sqlda-name\>*

</b></dt>
<dd>

Identifier.



</dd><dt><b>

*<into-sqlda-name\>*

</b></dt>
<dd>

Identifier.



</dd><dt><b>

*<statement\>*

</b></dt>
<dd>

String or host-variable.



</dd><dt><b>

USING

</b></dt>
<dd>

OUTPUT from a `SELECT` statement or a `CALL` statement is put either into the variables in the variable list or into the program data areas described by the named SQLDA. The correspondence is one to one from the OUTPUT \(selection list or parameters\) to either the host variable list or the SQLDA descriptor array.



</dd><dt><b>

INTO

</b></dt>
<dd>

If used with an `INSERT` statement, the inserted row is returned in the second descriptor. For example, when using autoincrement primary keys that generate primary-key values, `EXECUTE` provides a mechanism to refetch the row immediately and determine the primary-key value assigned to the row.



</dd><dt><b>

ARRAH

</b></dt>
<dd>

Used with prepared `INSERT` statements to allow wide inserts, which insert more than one row at a time and which might improve performance. The value nnn is the number of rows to be inserted. The SQLDA must contain nnn \* \(columns per row\) variables. The first row is placed in SQLDA variables 0 to \(columns per row\)-1, and so on. Similarly, the ARRAY clause can be used for wide updates, deletes, and merges using prepared UPDATE, DELETE, and MERGE statements.



</dd>
</dl>



<a name="loioa774406384f21015b6b5b37c393396c9__IQ_Usage"/>

## Remarks

Syntax 1 – If the dynamic statement contains host variable placeholders, which supply information for the request \(bind variables\), then either the *<sqlda-name\>* must specify a C variable, which is a pointer to a SQLDA containing enough descriptors for all bind variables occurring in the statement, or the bind variables must be supplied in the *<host-variable-list\>*.

Syntax 2 – The SQL statement contained in the string or host variable is immediately executed and is dropped on completion.

`EXECUTE` can be used for any SQL statement that can be prepared. Cursors are used for `SELECT` statements or `CALL` statements that return many rows from the database.

After successful execution of an `INSERT`, `UPDATE`, or `DELETE` statement, the sqlerrd\[2\] field of the SQLCA \(SQLCOUNT\) is filled in with the number of rows affected by the operation.



<a name="loioa774406384f21015b6b5b37c393396c9__IQ_Permissions"/>

## Privileges

The required privileges depend on the statement being executed.



<a name="loioa774406384f21015b6b5b37c393396c9__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by Open Client/Open Server



<a name="loioa774406384f21015b6b5b37c393396c9__IQ_Examples"/>

## Examples

-   The following example executes a `DELETE`:

    ```
    EXEC SQL EXECUTE IMMEDIATE
    'DELETE FROM Employees WHERE EmployeeID = 105';
    ```

-   The following example executes a prepared `DELETE` statement:

    ```
    EXEC SQL PREPARE del_stmt FROM
    'DELETE FROM Employees WHERE EmployeeID = :a';
    EXEC SQL EXECUTE del_stmt USING :employee_number;
    ```

-   The following example executes a prepared query:

    ```
    EXEC SQL PREPARE sel1 FROM
    'SELECT Surname FROM Employees WHERE EmployeeID = :a';
    EXEC SQL EXECUTE sel1 USING :employee_number INTO :emp_lname;
    ```


**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[PREPARE Statement \[ESQL\] for Data Lake Relational Engine](prepare-statement-esql-for-data-lake-relational-engine-a621eea.md "Prepares a statement to be executed later or used for a cursor.")

