<!-- loioa61bb2cb84f21015923297bc8b650772 -->

# DESCRIBE Statement \[ESQL\] for Data Lake Relational Engine

Gets information about the host variables required to store data retrieved from the database or host variables used to pass data to the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DESCRIBE
   …[ USER TYPES ]
   …[ { ALL | BIND VARIABLES FOR | INPUT | OUTPUT | SELECT LIST FOR } ]
   …[ { LONG NAMES [ <long-name-spec> ] | WITH VARIABLE RESULT } ]
   …[ FOR ] { <statement-name> | CURSOR <cursor-name> }
   …INTO <sqlda-name>
```

```
<long-name-spec> ::=
   { OWNER.TABLE.COLUMN 
   | TABLE.COLUMN 
   | COLUMN }
```



<a name="loioa61bb2cb84f21015923297bc8b650772__IQ_Parameters"/>

## Parameters

 USER TYPES
 :   Returns information about user-defined data types of a column. Typically, such a `DESCRIBE` is done when a previous `DESCRIBE` returns an indicator of DT\_HAS\_USERTYPE\_INFO.

    The information returned is the same as for a `DESCRIBE` without the USER TYPES clause, except that the sqlname field holds the name of the user-defined data type, instead of the name of the column.

    If `DESCRIBE` uses the LONG NAMES clause, the sqldata field holds this information.

  ALL
 :   Describes INPUT and OUTPUT with one request to the database server. This has a performance benefit in a multiuser environment. The INPUT information is filled in the SQLDA first, followed by the OUTPUT information. The sqld field contains the total number of INPUT and OUTPUT variables. The DT\_DESCRIBE\_INPUT bit in the indicator variable is set for INPUT variables and clear for OUTPUT variables.

  BIND VARIABLES FOR
 :   Equivalent to the INPUT clause. When used with the INPUT clause, DESCRIBE BIND VARIABLES does not set up the data types in the SQLDA: this needs to be done by the application.

  INPUT
 :   Fills in the name fields in the SQLDA with the bind variable names. A bind variable is a value supplied by the application when the database executes the statements. Bind variables can be considered parameters to the statement. INPUT clause also puts the number of bind variables in the sqld field of the SQLDA.

    `DESCRIBE` uses the indicator variables in the SQLDA to provide additional information. DT\_PROCEDURE\_IN and DT\_PROCEDURE\_OUT are bits that are set in the indicator variable when a `CALL` statement is described. DT\_PROCEDURE\_IN indicates an IN or INOUT parameter and DT\_PROCEDURE\_OUT indicates an INOUT or OUT parameter. Procedure RESULT columns have both bits clear. After a DESCRIBE OUTPUT, these bits can be used to distinguish between statements that have result sets \(need to use `OPEN`, `FETCH`, `RESUME`, `CLOSE`\) and statements that do not \(need to use `EXECUTE`\). DESCRIBE INPUT sets DT\_PROCEDURE\_IN and DT\_PROCEDURE\_OUT appropriately only when a bind variable is an argument to a `CALL` statement; bind variables within an expression that is an argument in a `CALL` statement sets the bits.

  OUTPUT
 :   Fills in the data type and length in the SQLDA for each select list item. The name field is also filled in with a name for the select list item. If an alias is specified for a select list item, the name is that alias. Otherwise, the name derives from the select list item: if the item is a simple column name, it is used; otherwise, a substring of the expression is used. `DESCRIBE` also puts the number of select list items in the sqld field of the SQLDA.

    -   If the statement being described is a UNION of two or more `SELECT` statements, the column names returned for DESCRIBE OUTPUT are the same column names which would be returned for the first `SELECT` statement.
    -   If you describe a CALL statement, DESCRIBE OUTPUT fills in the data type, length, and name in the SQLDA for each INOUT or OUT parameter in the procedure. DESCRIBE OUTPUT also puts the number of INOUT or OUT parameters in the sqld field of the SQLDA.
    -   If you describe a CALL statement with a result set, OUTPUT fills in the data type, length, and name in the SQLDA for each RESULT column in the procedure definition. DESCRIBE OUTPUT also puts the number of result columns in the sqld field of the SQLDA.

  SELECT LIST FOR
 :   Equivalent to the OUTPUT clause.

  LONG NAMES \[ *<long-name-spec\>* \]
 :   Retrieves column names for a statement or cursor. Without this clause, there is a 29-character limit on the length of column names: with the clause, names of an arbitrary length are supported. If LONG NAMES is used, the long names are placed into the SQLDATA field of the SQLDA, as if you were fetching from a cursor. None of the other fields \(SQLLEN, SQLTYPE, and so on\) are filled in. The SQLDA must be set up like a `FETCH` SQLDA: it must contain one entry for each column, and the entry must be a string type. The default specification for the long names is TABLE.COLUMN.

  WITH VARIABLE RESULT
 :   Describes procedures that might have more than one result set, with different numbers or types of columns. If WITH VARIABLE RESULT is used, the database server sets the SQLCOUNT value after the describe to one of these values:

    -   0 – the result set may change. The procedure call should be described again following each `OPEN` statement.
    -   1 – the result set is fixed. You need not describe again.

  *<statement-name\>*
 :   Identifier or host-variable. If you specify a statement name, the statement must have been previously prepared using the `PREPARE` statement with the same statement name.

  CURSOR *<cursor-name\>*
 :   Declared cursor. The cursor must have been previously declared and opened. The default action is to describe the OUTPUT. Only `SELECT` statements and `CALL` statements have OUTPUT. A DESCRIBE OUTPUT on any other statement, or on a cursor that is not a dynamic cursor, indicates no output by setting the sqld field of the SQLDA to zero.

  INTO *<sqlda-name\>*
 :   Identifier

 

<a name="loioa61bb2cb84f21015923297bc8b650772__IQ_Usage"/>

## Remarks

`DESCRIBE` sets up the named SQLDA to describe either the OUTPUT \(equivalently `SELECT LIST`\) or the INPUT \(BIND VARIABLES\) for the named statement.



<a name="loioa61bb2cb84f21015923297bc8b650772__IQ_Permissions"/>

## Privileges

None



<a name="loioa61bb2cb84f21015923297bc8b650772__IQ_Standards"/>

## Standards

The following applies to some clauses:

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61bb2cb84f21015923297bc8b650772__IQ_Examples"/>

## Examples

-   The following example shows how to use the `DESCRIBE` statement:

    ```
    sqlda = alloc_sqlda( 3 );
    EXEC SQL DESCRIBE OUTPUT 
      FOR employee_statement 
      INTO sqlda;
    if( sqlda->sqld  >  sqlda->sqln ) {
      actual_size = sqlda->sqld;
      free_sqlda( sqlda );
      sqlda = alloc_sqlda( actual_size );
      EXEC SQL DESCRIBE OUTPUT 
        FOR employee_statement 
        INTO sqlda;
    }
    ```


**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[OPEN Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](open-statement-esql-sp-for-data-lake-relational-engine-a6215ad.md "Opens a previously declared cursor to access information from the database.")

[PREPARE Statement \[ESQL\] for Data Lake Relational Engine](prepare-statement-esql-for-data-lake-relational-engine-a621eea.md "Prepares a statement to be executed later or used for a cursor.")

