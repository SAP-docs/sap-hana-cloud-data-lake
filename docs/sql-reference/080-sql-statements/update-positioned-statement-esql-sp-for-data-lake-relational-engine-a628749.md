<!-- loioa628749684f21015958edc0cde107b63 -->

# UPDATE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Modifies the data at the current location of a cursor.



<a name="loioa628749684f21015958edc0cde107b63__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
UPDATE <table-list> 
   SET <set-item> [, ...]
   WHERE CURRENT OF <cursor-name>
```

```
<set-item> ::=
   <column-name> [.<field-name>…] = <scalar-value>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa628749684f21015958edc0cde107b63__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<cursor-name\>*

</b></dt>
<dd>

Identifier or hostvar.



</dd><dt><b>

SET

</b></dt>
<dd>

The columns that are referenced in set-item must be in the base table that is updated. They cannot refer to aliases, nor to columns from other tables or views. If the table you are updating is given a correlation name in the cursor specification, you must use the correlation name in the SET clause. The expression on the right side of the SET clause may reference columns, constants, variables, and expressions from the `SELECT` clause of the query.



</dd><dt><b>

*<set-item\>*

</b></dt>
<dd>

Expression cannot contain functions or expressions.



</dd><dt><b>

WHERE CURRENT OF

</b></dt>
<dd>

Avoid using ORDER BY in the WHERE CURRENT OF clause. The ORDER BY columns may be updated, but the result set does not reorder. The results appear to fetch out of order and appear to be incorrect.



</dd>
</dl>



This example shows an `UPDATE` statement using WHERE CURRENT OF cursor:

```
UPDATE Employees SET surname = 'Jones'
WHERE CURRENT OF emp_cursor;
```



<a name="loioa628749684f21015958edc0cde107b63__IQ_Usage"/>

## Remarks

This form of the `UPDATE` statement updates the current row of the specified cursor. The current row is defined to be the last row successfully fetched from the cursor, and the last operation on the cursor cannot have been a positioned `DELETE` statement.

The requested columns are set to the specified values for the row at the current row of the specified query. The columns must be in the select list of the specified open cursor.

Changes effected by positioned `UPDATE` statements are visible in the cursor result set, except where client-side caching prevents seeing these changes. Rows that are updated so that they no longer meet the requirements of the WHERE clause of the open cursor are still visible.

Since data lake Relational Engine does not support the `CREATE VIEW... WITH CHECK OPTION`, positioned `UPDATE` does not support this option. The WITH CHECK OPTION clause does not allow an update that creates a row that is not visible by the view.

A rowid column cannot be updated by a positioned `UPDATE`.

Data lake Relational Engine supports repeatedly updating the same row in the result set.



<a name="loioa628749684f21015958edc0cde107b63__IQ_Permissions"/>

## Privileges

Requires UPDATE object-level permission on the columns being modified.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa628749684f21015958edc0cde107b63__IQ_Standards"/>

## Standards

-   The range of cursors that can be updated may contain vendor extensions to ISO/ANSI SQL grammar if the ANSI\_UPDATE\_CONSTRAINTS option is set to OFF.
-   Embedded SQL use is supported by Open Client/Open Server, and procedure and trigger use is supported in SAP SQL Anywhere.

**Related Information**  


[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[DELETE Statement for Data Lake Relational Engine](delete-statement-for-data-lake-relational-engine-a61b555.md "Deletes all the rows from the named table that satisfy the search condition. If no WHERE clause is specified, all rows from the named table are deleted.")

[DELETE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](delete-positioned-statement-esql-sp-for-data-lake-relational-engine-a61b84a.md "Deletes the data at the current location of a cursor.")

[UPDATE Statement for Data Lake Relational Engine](update-statement-for-data-lake-relational-engine-a628441.md "Modifies existing rows of a single table, or a view that contains only one table.")

