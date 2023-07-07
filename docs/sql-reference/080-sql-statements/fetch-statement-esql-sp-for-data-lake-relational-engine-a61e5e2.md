<!-- loioa61e5e2484f2101598b898b5613275f6 -->

# FETCH Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Retrieves one row from the named cursor. The cursor must have been previously opened.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
FETCH
   { NEXT | PRIOR | FIRST | LAST
   | ABSOLUTE <row-count> | RELATIVE <row-count> }
   ... <cursor-name>
   ... { [ INTO <host-variable-list> ]
       | USING DESCRIPTOR <sqlda-name>
       | INTO <variable-list> }
   ... [ PURGE ] [ BLOCK <n> ] [ ARRAY <fetch-count> ]
   ... INTO <variable-list>
   ... IQ CACHE <row-count>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61e5e2484f2101598b898b5613275f6__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

NEXT

</b></dt>
<dd>

\(Default\) Causes the cursor to advance one row before the row is fetched.



</dd><dt><b>

PRIOR

</b></dt>
<dd>

Moves the cursor back one row before fetching.



</dd><dt><b>

ABSOLUTE *<row-count\>*

</b></dt>
<dd>

Used to go to a particular row. A zero indicates the position before the first row.

A one \(1\) indicates the first row, and so on. Negative numbers are used to specify an absolute position from the end of the cursor. A negative one \(-1\) indicates the last row of the cursor. FIRST is a short form for ABSOLUTE 1. LAST is a short form for ABSOLUTE -1.

> ### Note:  
> Data lake Relational Engine handles the FIRST, LAST, ABSOLUTE, and negative RELATIVE clauses less efficiently than some other DBMS products, so there is a performance impact when using them.



</dd><dt><b>

RELATIVE

</b></dt>
<dd>

Moves the cursor by a specified number of rows in either direction before fetching.

A positive number indicates moving forward and a negative number indicates moving backwards. Thus, a NEXT is equivalent to RELATIVE 1 and PRIOR is equivalent to RELATIVE -1. RELATIVE 0 retrieves the same row as the last fetch statement on this cursor.



</dd><dt><b>

*<row-count\>*

</b></dt>
<dd>

Number or host variable



</dd><dt><b>

*<cursor-name\>*

</b></dt>
<dd>

Identifier or host variable



</dd><dt><b>

INTO *<host-variable-list\>*

</b></dt>
<dd>

\(Embedded SQL only\) May contain indicator variables



</dd><dt><b>

USING DESCRIPTOR *<sqlda-name\>*

</b></dt>
<dd>

\(Embedded SQL only\) Identifier



</dd><dt><b>

*<fetch-count\>*

</b></dt>
<dd>

Integer or host variable



</dd><dt><b>

INTO *<variable-list\>*

</b></dt>
<dd>

If it is not specified, then `FETCH` positions the cursor only .OPEN initially positions the cursor before the first row. An optional positional parameter can be specified that allows the cursor to be moved before a row is fetched.



</dd><dt><b>

PURGE

</b></dt>
<dd>

\(Embedded SQL only\) Causes the client to flush its buffers of all rows and then send the fetch request to the server. This fetch request may return a block of rows.



</dd><dt><b>

BLOCK *<n\>*

</b></dt>
<dd>

\(Embedded SQL only\) Gives the client and server a hint as to how many rows may be fetched by the application. The special value of 0 means the request is sent to the server and a single row is returned \(no row blocking\).



</dd>
</dl>


<dl>
<dt><b>

ARRAY *<fetch-count\>*

</b></dt>
<dd>

\(Embedded SQL only\) Allows wide fetches, which retrieve more than one row at a time, and which might improve performance. To use wide fetches in Embedded SQL, include the `FETCH` statement in your code, where `ARRAY nnn` is the last item of the `FETCH` statement:

```
EXEC SQL FETCH . . . ARRAY nnn
```

The fetch count nnn can be a host variable. The SQLDA must contain nnn \* \(columns per row\) variables. The first row is placed in SQLDA variables 0 to \(columns per row\) -1, and so on.



</dd><dt><b>

IQ CACHE *<row-count\>*

</b></dt>
<dd>

Specifies the maximum number of rows buffered in the FIFO queue. If you do not specify a value for IQ CACHE, the value of the `CURSOR_WINDOW_ROWS` database option is used. The default setting of `CURSOR_WINDOW_ROWS` is 200.



</dd>
</dl>



<a name="loioa61e5e2484f2101598b898b5613275f6__IQ_Usage"/>

## Remarks

These clauses are for use in Embedded SQL only:

-   <code>USING DESCRIPTOR <i class="varname">&lt;sqlda-name&gt;</i></code>
-   <code>INTO <i class="varname">&lt;host-variable-list&gt;</i></code>
-   `PURGE`
-   <code>BLOCK <i class="varname">&lt;n&gt;</i></code>
-   <code>ARRAY <i class="varname">&lt;fetch-count&gt;</i></code>
-   Use of *<host-variable\>* in *<cursor-name\>* and *<row-count\>*

One row from the result of `SELECT` is put into the variables in the variable list. The correspondence from the select list to the host variable list is one-to-one.

One or more rows from the result of `SELECT` are put either into the variables in the variable list or into the program data areas described by the named SQLDA. In either case, the correspondence from the select list to either the host variable list or the SQLDA descriptor array is one-to-one.

A cursor declared FOR READ ONLY sees the version of table\(s\) on which the cursor is declared when the cursor is opened, not the version of table\(s\) at the time of the first `FETCH`

If the `FETCH` includes a positioning parameter and the position is outside the allowable cursor positions, then the SQLE\_NOTFOUND warning is issued.

`DECLARE CURSOR` must appear before `FETCH` in the C source code, and the `OPEN` statement must be executed before `FETCH`. If a host variable is being used for the cursor name, then the `DECLARE` statement actually generates code and thus must be executed before `FETCH`.

In the multiuser environment, rows can be fetched by the client more than one at a time. This is referred to as block fetching or multirow fetching. The first fetch causes several rows to be sent back from the server. The client buffers these rows and subsequent fetches are retrieved from these buffers without a new request to the server.

If the SQLSTATE\_NOTFOUND warning is returned on the fetch, then the sqlerrd\[2\] field of the SQLCA \(SQLCOUNT\) contains the number of rows that the attempted fetch exceeded the allowable cursor positions. \(A cursor can be on a row, before the first row or after the last row.\) The value is 0 if the row was not found but the position is valid, for example, executing `FETCH` with a RELATIVE 1 clause when positioned on the last row of a cursor. The value is positive if the attempted fetch was further beyond the end of the cursor, and negative if the attempted fetch was further before the beginning of the cursor.

After successful execution of the `FETCH` statement, the sqlerrd\[1\] field of the SQLCA \(SQLIOCOUNT\) is incremented by the number of input/output operations required to perform the fetch. This field is actually incremented on every database statement.

The server returns in SQLCOUNT the number of records fetched and always returns a SQLCOUNT greater than zero unless there is an error. Older versions of the server only return a single row and the SQLCOUNT is set to zero. Thus a SQLCOUNT of zero with no error condition indicates one valid row has been fetched.



<a name="loioa61e5e2484f2101598b898b5613275f6__IQ_Permissions"/>

## Privileges

The cursor must be opened and you must have SELECT object-level permission on the tables referenced in the declaration of the cursor.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa61e5e2484f2101598b898b5613275f6__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa61e5e2484f2101598b898b5613275f6__IQ_Examples"/>

## Examples

-   The following is an embedded SQL example:

    ```
    EXEC SQL DECLARE cur_employee CURSOR FOR
    SELECT EmployeeID, Surname FROM Employees;
    EXEC SQL OPEN cur_employee;
    EXEC SQL FETCH cur_employee
    INTO :emp_number, :emp_name:indicator;
    ```

-   The following is a procedure example:

    ```
    BEGIN
    	DECLARE cur_employee CURSOR FOR
    		SELECT Surname
    		FROM Employees;
    	DECLARE name CHAR(40) ;
    	OPEN cur_employee;
    	LOOP
    		FETCH NEXT cur_employee into name ;
    		 .
    		 .
    		 .
    	END LOOP
    	CLOSE cur_employee;
    END
    ```


**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[OPEN Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](open-statement-esql-sp-for-data-lake-relational-engine-a6215ad.md "Opens a previously declared cursor to access information from the database.")

[PREPARE Statement \[ESQL\] for Data Lake Relational Engine](prepare-statement-esql-for-data-lake-relational-engine-a621eea.md "Prepares a statement to be executed later or used for a cursor.")

[CURSOR\_WINDOW\_ROWS Option for Data Lake Relational Engine](../090-database-options/cursor-window-rows-option-for-data-lake-relational-engine-a631f60.md "Defines the number of cursor rows to buffer.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

