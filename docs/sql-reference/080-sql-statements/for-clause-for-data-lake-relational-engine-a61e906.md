<!-- loioa61e906784f210158fadf7350f8470f5 -->

# FOR Clause for Data Lake Relational Engine

Repeats the execution of a statement list once for each row in a cursor.



<a name="loioa61e906784f210158fadf7350f8470f5__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement clause can be used when connected as follows:

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



<a name="loioa61e906784f210158fadf7350f8470f5__for_clause_parameters1"/>

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



<a name="loioa61e906784f210158fadf7350f8470f5__for_clause_remarks1"/>

## Remarks

FOR is a control statement that lets you execute a list of SQL statements once for each row in a cursor.

The FOR statement is equivalent to a compound statement with a DECLARE for the cursor and a DECLARE of a variable for each column in the result set of the cursor, followed by a loop that fetches one row from the cursor into the local variables and executes *<statement-list\>* once for each row in the cursor.

The name and data type of the local variables that are declared are derived from the *<statement\>* used in the cursor. With a SELECT statement, the data type is the data type of the expressions in the select list. The names are the select list item aliases where they exist; otherwise, they are the names of the columns. Any select list item that is not a simple column reference must have an alias. With a CALL statement, the names and data types are taken from the RESULT clause in the procedure definition.

The LEAVE statement can be used to resume execution at the first statement after the END FOR. If the ending *<statement-label\>* is specified, it must match the beginning *<statement-label\>*.



<a name="loioa61e906784f210158fadf7350f8470f5__for_clause_privileges1"/>

## Privileges



### 

No additional privileges are required beyond those required by the SELECT statement



<a name="loioa61e906784f210158fadf7350f8470f5__for_clause_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa61e906784f210158fadf7350f8470f5__for_clause_examples1"/>

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


[FROM Clause for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/ccd090fa57a84916b181a47c6ba634e1.html "Specifies the objects involved in a SELECT, DELETE or UPDATE statement.") :arrow_upper_right:

