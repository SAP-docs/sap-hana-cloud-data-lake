<!-- loio81b173b0076b467d85548be9e1da14fa -->

# FOR Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Repeats the execution of a statement list once for each row in a cursor.



<a name="loio81b173b0076b467d85548be9e1da14fa__section_c44_3gs_wbc"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement clause can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
[ <statement-label>: ]
   FOR <for-loop-name> AS <cursor-name> [ <cursor-type> ] CURSOR
      { FOR <statement>
      ... [ { FOR { UPDATE BY { VALUES | TIMESTAMP | LOCK } | FOR READ ONLY } ]
      | USING <variable-name> }
   DO <statement-list>
   END FOR [ <statement-label> ]
```

```
<cursor-type> ::=
   { NO SCROLL  
   | DYNAMIC SCROLL  
   | SCROLL  
   | INSENSITIVE  
   | SENSITIVE }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio81b173b0076b467d85548be9e1da14fa__section_wrv_lgs_wbc"/>

## Parameters


<dl>
<dt><b>

NO SCROLL

</b></dt>
<dd>

A cursor declared NO SCROLL is restricted to moving forward through the result set using FETCH NEXT and FETCH RELATIVE 0 seek operations. As rows cannot be returned to once the cursor leaves the row, there are no sensitivity restrictions on the cursor. When a NO SCROLL cursor is requested, the database server supplies the most efficient kind of cursor, which is an asensitive cursor.



</dd><dt><b>

DYNAMIC SCROLL

</b></dt>
<dd>

DYNAMIC SCROLL is the default cursor type. DYNAMIC SCROLL cursors can use all formats of the FETCH statement. When a DYNAMIC SCROLL cursor is requested, the database server supplies an asensitive cursor. When using cursors there is always a trade-off between efficiency and consistency. Asensitive cursors provide efficient performance at the expense of consistency.



</dd><dt><b>

SCROLL

</b></dt>
<dd>

A cursor declared SCROLL can use all formats of the FETCH statement. When a SCROLL cursor is requested, the database server supplies a value-sensitive cursor. The database server must execute value-sensitive cursors in such a way that result set membership is guaranteed. DYNAMIC SCROLL cursors are more efficient and should be used unless the consistent behavior of SCROLL cursors is required



</dd><dt><b>

INSENSITIVE

</b></dt>
<dd>

A cursor declared INSENSITIVE has its values and membership fixed over its lifetime. The result set of the SELECT statement is materialized when the cursor is opened. FETCHING from an INSENSITIVE cursor does not see the effect of any other INSERT, UPDATE, MERGE, PUT, or DELETE statement from any connection, including the connection that opened the cursor.



</dd><dt><b>

SENSITIVE

</b></dt>
<dd>

A cursor declared SENSITIVE is sensitive to changes to membership or values of the result set.



</dd>
</dl>



<a name="loio81b173b0076b467d85548be9e1da14fa__section_f2t_mgs_wbc"/>

## Remarks

FOR is a control statement that lets you execute a list of SQL statements once for each row in a cursor.

The FOR statement is equivalent to a compound statement with a DECLARE for the cursor and a DECLARE of a variable for each column in the result set of the cursor, followed by a loop that fetches one row from the cursor into the local variables and executes *<statement-list\>* once for each row in the cursor.

The name and data type of the local variables that are declared are derived from the *<statement\>* used in the cursor. With a SELECT statement, the data type is the data type of the expressions in the select list. The names are the select list item aliases where they exist; otherwise, they are the names of the columns. Any select list item that is not a simple column reference must have an alias. With a CALL statement, the names and data types are taken from the RESULT clause in the procedure definition.

The LEAVE statement can be used to resume execution at the first statement after the END FOR. If the ending *<statement-label\>* is specified, it must match the beginning *<statement-label\>*.



<a name="loio81b173b0076b467d85548be9e1da14fa__section_ezk_ngs_wbc"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

No additional privileges are required beyond those required by the SELECT statement



</dd>
</dl>



<a name="loio81b173b0076b467d85548be9e1da14fa__section_wgg_xgs_wbc"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio81b173b0076b467d85548be9e1da14fa__section_sfh_1hs_wbc"/>

## Examples

This code fragment illustrates the use of the FOR loop:

```
FOR names AS curs CURSOR FOR
SELECT Surname
FROM Employees
DO
   CALL search_for_name( Surname );
END FOR;
```

**Related Information**  


[FOR Clause for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a61e906784f210158fadf7350f8470f5.html "Repeats the execution of a statement list once for each row in a cursor.") :arrow_upper_right:

