<!-- loioa61ac0bc84f21015aa8bc3dddd3b73d4 -->

# DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Declares a cursor. Cursors are the primary means for manipulating the results of queries.



<a name="loioa61ac0bc84f21015aa8bc3dddd3b73d4__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DECLARE <cursor-name>
   [ { SCROLL
     | NO SCROLL 
     | DYNAMIC SCROLL } ]
   CURSOR FOR
   { <select-statement> FOR { READ ONLY | UPDATE }
   | <statement-name>   
   | USING <variable-name> }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61ac0bc84f21015aa8bc3dddd3b73d4__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<statement-name\>*

</b></dt>
<dd>

Identifier or host-variable. Statements are named using the `PREPARE` statement. Cursors can be declared only for a prepared `SELECT` or `CALL`.



</dd><dt><b>

SCROLL

</b></dt>
<dd>

A cursor declared as SCROLL supports the NEXT, PRIOR, FIRST, LAST, ABSOLUTE, and RELATIVE options of the `FETCH` statement. A SCROLL cursor lets you fetch an arbitrary row in the result set while the cursor is open.



</dd><dt><b>

NO SCROLL

</b></dt>
<dd>

A cursor declared as NO SCROLL is restricted to moving forward through the result set using only the `FETCH NEXT` and `FETCH ABSOLUTE (0)` seek operations.



</dd><dt><b>

DYNAMIC SCROLL

</b></dt>
<dd>

A cursor declared as DYNAMIC SCROLL supports the NEXT, PRIOR, FIRST, LAST, ABSOLUTE, and RELATIVE clauses of the `FETCH` statement. A DYNAMIC SCROLL cursor lets you fetch an arbitrary row in the result set while the cursor is open.

Since rows cannot be returned to once the cursor leaves the row, there are no sensitivity restrictions on the cursor. Consequently, when a NO SCROLL cursor is requested, data lake Relational Engine supplies the most efficient kind of cursor, which is an asensitive cursor.



</dd><dt><b>

READ ONLY

</b></dt>
<dd>

\(Default\) A cursor declared FOR READ ONLY may not be used in a positioned `UPDATE` or a positioned `DELETE` operation.



</dd>
<dd>

A cursor declared FOR READ ONLY sees the version of table\(s\) on which the cursor is declared when the cursor is opened, not the version of table\(s\) at the time of the first `FETCH`.

For example, when the cursor is fetched, only one row can be fetched from the table:

```
CREATE TABLE t1 ( c1 INT );
INSERT t1 VALUES ( 1 );

BEGIN
DECLARE t1_cursor CURSOR FOR SELECT * FROM t1
FOR READ ONLY;
OPEN t1_cursor;
INSERT t1 VALUES ( 2 );
FETCH T1_CURSOR;
END;
```



</dd><dt><b>

UPDATE

</b></dt>
<dd>

You can update the cursor result set of a cursor declared FOR UPDATE. Only asensitive behavior is supported for updatable cursors; any other sensitivity is ignored.

When the cursor is opened, exclusive table locks are taken on all tables that are opened for update. Standalone `LOAD TABLE`, `UPDATE`, `INSERT`, `DELETE`, and `TRUNCATE` statements are not allowed on tables that are opened for update in the same transaction, since data lake Relational Engine permits only one statement to modify a table at a time. You can open only one updatable cursor on a specific table at a time.

Updatable cursors are allowed to scroll, except over Open Client.



</dd><dt><b>

USING

</b></dt>
<dd>

You can declare a cursor on a variable in stored procedures and user-defined functions. The variable is a string containing a `SELECT` statement for the cursor. The variable must be available when the `DECLARE` is processed, and so must be one of the following:

```
create function get_row_count(in qry varchar)
returns int
begin
    declare crsr cursor using qry;
    declare rowcnt int;

    set rowcnt = 0;
    open crsr;
    lp: loop
        fetch crsr;
        if SQLCODE <> 0 then leave lp end if;
        set rowcnt = rowcnt + 1;
    end loop;
    return rowcnt;
end;
```

Nested inside another `BEGIN…END` after the variable has been assigned a value. For example:

```
create procedure get_table_name(
  in id_value int, out tabname char(128))

begin
  declare qry varchar;

  set qry = 'select table_name from SYS.ISYSTAB ' ||
        'where table_id=' || string(id_value);
  begin
    declare crsr cursor using qry;

    open crsr;
    fetch crsr into tabname;
    close crsr;
 end
end;
```



</dd>
</dl>



<a name="loioa61ac0bc84f21015aa8bc3dddd3b73d4__IQ_Usage"/>

## Remarks

The `DECLARE CURSOR` statement declares a cursor with the specified name for a `SELECT` statement or a `CALL` statement.

Embedded SQL statements are named using the `PREPARE` statement. Cursors can be declared only for a prepared `SELECT` or `CALL`.

Data lake Relational Engine supports updatable cursors on single tables.

Data lake Relational Engine supports one type of cursor sensitivity, which is defined in terms of which changes to underlying data are visible. All data lake Relational Engine cursors are asensitive, which means that changes might be reflected in the membership, order, or values of the result set seen through the cursor, or might not be reflected at all.

With an asensitive cursor, changes effected by positioned `UPDATE` and positioned `DELETE` statements are visible in the cursor result set, except where client-side caching prevents seeing these changes. Inserted rows aren't visible.

Rows that are updated so that they no longer meet the requirements of the `WHERE` clause of the open cursor are still visible.

When using cursors, there's always a trade-off between efficiency and consistency. Asensitive cursors provide efficient performance at the expense of consistency.

`LONG VARCHAR` and `LONG BINARY` data types aren't supported in updatable cursors.

Scalar user-defined functions and user-defined aggregate functions aren't supported in updatable cursors.

Supported query specifications for updatable cursors in data lake Relational Engine are:

-   Expressions in the select list against columns that aren't functionally dependent on columns being updated
-   Arbitrary subqueries with asensitive behavior, that is, changes to data referenced by subqueries aren't visible in the cursor result set
-   `ORDER BY` clause; the `ORDER BY` columns may be updated, but the result set doesn't reorder
-   Columns that meet these requirements:
    -   No CAST on a column
    -   Base columns of a base table in the `SELECT` clause
    -   There are no expressions or functions on that column in the `SELECT` clause and it isn't duplicated in the select list \(for example, `SELECT c1, c1`\).
    -   Base columns of a base table restricted to those listed in the <code>FOR UPDATE OF <i class="varname">&lt;column-name-list&gt;</i></code> clause, if the clause is specified.


Data lake Relational Engine doesn’t permit updatable cursors on queries that contain any operator that precludes a one-to-one mapping of result set rows to rows in a base table; specifically:

-   `SELECT DISTINCT`
-   Operator that has a `UNION`
-   Operator that has a `GROUP BY`
-   Operator that has a `SET` function
-   Operator that has an `OLAP` function, with the exception of `RANK()`

See the description of the *UPDATE \(positioned\) Statement \[ESQL\] \[SP\]* for information on the columns and expressions allowed in the `SET` clause for the update of a row in the result set of a cursor.

Data lake Relational Engine supports inserts only on updatable cursors where all nonnullable, nonidentity columns are both selected and updatable.

In data lake Relational Engine, `COMMIT` and `ROLLBACK` aren't allowed inside an open updatable cursor, even if the cursor is opened as a hold cursor. Data lake Relational Engine does support `ROLLBACK TO SAVEPOINT` inside an updatable cursor.

Any failure that occurs after the cursor is open results in a rollback of all operations that have been performed through this open cursor.

Updatable Cursor Limitations

A declared cursor is read-only and not updatable in cases where:

-   The data extraction facility is enabled with the `TEMP_EXTRACT_NAME1` option set to a pathname
-   `ANSI_CLOSE_CURSORS_ON_ROLLBACK` is set OFF
-   CHAINED is set OFF
-   The statement is `INSERT SELECT` or `SELECT INTO`
-   More than one table is included
-   No updatable columns exist

If data lake Relational Engine fails to set an updatable cursor when requested, see the `.iqmsg` file for related information.

There's a limitation regarding updatable cursors and ODBC. A maximum of 65535 rows or records can be updated, deleted, or inserted at a time using these ODBC functions:

-   `SQLSetPos` `SQL_UPDATE`, `SQL_DELETE`, and `SQL_ADD`
-   `SQLBulkOperations` `SQL_ADD`, `SQL_UPDATE_BY_BOOKMARK`, and `SQL_DELETE_BY_BOOKMARK`

There's an implementation-specific limitation to the maximum value in the statement attribute that controls the number of effected rows to the largest value of an `UNSIGNED SMALL INT`, which is 65535:

```
SQLSetStmtAttr(HANDLE,SQL_ATTR_ROW_ARRAY_SIZE, VALUE,0);
```

Data lake Relational Engine updatable cursors differ from ANSI SQL3 standard behavior as follows:

-   Hold cursor update close on commit.
-   Data lake Relational Engine locks tables when the cursor is open.
-   All updates, deletes, and insert operations are applied when the cursor is closed, in this order: deletes first, then updates, then inserts.

> ### Note:  
> Use the `sp_iqcursorinfo` system procedure to display detailed information about cursors currently open on the server.



<a name="loioa61ac0bc84f21015aa8bc3dddd3b73d4__IQ_Permissions"/>

## Privileges

None



<a name="loioa61ac0bc84f21015aa8bc3dddd3b73d4__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61ac0bc84f21015aa8bc3dddd3b73d4__IQ_Examples"/>

## Examples

-   The following example declares a scroll cursor in Embedded SQL:

    ```
    EXEC SQL DECLARE cur_employee SCROLL CURSOR 
    FOR SELECT * FROM Employees;
    ```

-   The following example declares a cursor for a prepared statement in Embedded SQL:

    ```
    EXEC SQL PREPARE employee_statement
    FROM 'SELECT emp_lname FROM Employees';
    EXEC SQL DECLARE cur_employee CURSOR 
    FOR employee_statement ;
    ```

-   The following example uses cursors in a stored procedure:

    ```
    BEGIN
      DECLARE cur_employee CURSOR FOR
          SELECT emp_lname
          FROM Employees;
      DECLARE name CHAR(40);
      OPEN cur_employee;
      LOOP
        FETCH NEXT cur_employee INTO name;
        ...
      END LOOP;
      CLOSE cur_employee;
    END;
    ```


**Related Information**  


[CALL Statement for Data Lake Relational Engine](call-statement-for-data-lake-relational-engine-a614c16.md "Invokes a procedure.")

[DELETE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](delete-positioned-statement-esql-sp-for-data-lake-relational-engine-a61b84a.md "Deletes the data at the current location of a cursor.")

[FETCH Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](fetch-statement-esql-sp-for-data-lake-relational-engine-a61e5e2.md "Retrieves one row from the named cursor. The cursor must have been previously opened.")

[OPEN Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](open-statement-esql-sp-for-data-lake-relational-engine-a6215ad.md "Opens a previously declared cursor to access information from the database.")

[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

[UPDATE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](update-positioned-statement-esql-sp-for-data-lake-relational-engine-a628749.md "Modifies the data at the current location of a cursor.")

[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[LEAVE Statement for Data Lake Relational Engine](leave-statement-for-data-lake-relational-engine-a6206e0.md "Continues execution by leaving a compound statement or LOOP.")

[LOOP Statement for Data Lake Relational Engine](loop-statement-for-data-lake-relational-engine-a620fd7.md "Repeats the execution of a statement list.")

