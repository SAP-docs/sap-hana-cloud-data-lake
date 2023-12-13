<!-- loioa61b84ab84f21015a60dd050d25ceb67 -->

# DELETE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Deletes the data at the current location of a cursor.



<a name="loioa61b84ab84f21015a60dd050d25ceb67__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DELETE [ FROM [ <owner>.]<correlation-name> ]
   WHERE CURRENT OF { <identifier> | <hostvar> };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61b84ab84f21015a60dd050d25ceb67__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

FROM

</b></dt>
<dd>

The table FROM which rows are deleted is determined as follows:

-   If no FROM clause is included, the cursor can only be on a single table.
-   If the cursor is for a joined query \(including using a view containing a join\), you must use the FROM clause. Only the current row of the specified table is deleted. The other tables involved in the join are not affected.
-   If you include a FROM clause and do not specify table owner, table-spec is first matched against any correlation names.
    -   If a correlation name exists, `table-spec` is identified with the correlation name.
    -   If a correlation name does not exist, `table-spec` must be unambiguously identifiable as a table name in the cursor.

-   If a FROM clause is included, and a table owner is specified, table-spec must be unambiguously identifiable as a table name in the cursor.



</dd>
</dl>



<a name="loioa61b84ab84f21015a60dd050d25ceb67__IQ_Usage"/>

## Remarks

This form of the `DELETE` statement deletes the current row of the specified cursor. The current row is defined to be the last row fetched from the cursor.

The positioned `DELETE` statement can be used on a cursor open on a view as long as the view is updatable.

Changes effected by positioned `DELETE` statements are visible in the cursor result set, except where client-side caching prevents seeing these changes.



<a name="loioa61b84ab84f21015a60dd050d25ceb67__IQ_Permissions"/>

## Privileges

Requires DELETE object-level privilege on tables used in the cursor.

See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges



<a name="loioa61b84ab84f21015a60dd050d25ceb67__IQ_Standards"/>

## Standards

-   SQL – the range of cursors that can be updated may contain vendor extensions to ISO/ANSI SQL grammar if the `ANSI_UPDATE_CONSTRAINTS` option is set to OFF.
-   SAP database products – Embedded SQL use is supported by Open Client/Open Server. Procedure and trigger use is supported in SAP SQL Anywhere.



<a name="loioa61b84ab84f21015a60dd050d25ceb67__IQ_Examples"/>

## Examples

The following example removes the current row from the database:

```
DELETE WHERE CURRENT OF cur_employee;
```

**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[INSERT Statement for Data Lake Relational Engine](insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[UPDATE Statement for Data Lake Relational Engine](update-statement-for-data-lake-relational-engine-a628441.md "Modifies existing rows of a single table, or a view that contains only one table.")

[UPDATE \(Positioned\) Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](update-positioned-statement-esql-sp-for-data-lake-relational-engine-a628749.md "Modifies the data at the current location of a cursor.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

