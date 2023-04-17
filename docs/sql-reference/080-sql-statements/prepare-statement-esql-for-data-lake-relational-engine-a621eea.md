<!-- loioa621eea184f210159e6ef52c2216ba0b -->

# PREPARE Statement \[ESQL\] for Data Lake Relational Engine

Prepares a statement to be executed later or used for a cursor.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
PREPARE <statement-name> 
   FROM <statement> [ FOR { READ ONLY | UPDATE [ OF <column-name-list> ] } ] 
   ... [ DESCRIBE <describe-type> INTO [ [ SQL ] DESCRIPTOR ] <descriptor> ]
   ... [ WITH EXECUTE ]
```

```
<describe-type> ::=
   { ALL 
   | BIND VARIABLES
   | INPUT 
   | OUTPUT 
   | SELECT LIST } ... { LONG NAMES [ [ OWNER.]TABLE.]COLUMN ] 
   | WITH VARIABLE RESULT }
```



<a name="loioa621eea184f210159e6ef52c2216ba0b__IQ_Parameters"/>

## Parameters

 *<statement-name\>*
 :   Referenced to execute the statement, or to open a cursor if the statement is a `SELECT` statement. *<statement-name\>* may be a host variable of type a\_sql\_statement\_number defined in the `sqlca.h` header file that is automatically included. If an identifier is used for the *<statement-name\>*, only one statement per module may be prepared with this *<statement-name\>*.

  FOR UPDATE | FOR READ ONLY
 :   Defines the cursor updatability if the statement is used by a cursor. A FOR READ ONLY cursor cannot be used in an `UPDATE` \(positioned\) or a `DELETE` \(positioned\) operation. FOR READ ONLY is the default. In response to any request for a cursor that specifies FOR UPDATE, data lake Relational Engine provides either a value-sensitive cursor or a sensitive cursor. Insensitive and asensitive cursors are not updatable.

  DESCRIBE INTO DESCRIPTOR
 :   The prepared statement is described into the specified descriptor. The describe type may be any of the describe types allowed in the `DESCRIBE` statement.

    The DESCRIBE INTO DESCRIPTOR clause might improve performance, as it decrease the required client/server communication.

  WITH EXECUTE
 :   The statement is executed if and only if it is not a `CALL` or `SELECT` statement, and it has no host variables. The statement is immediately dropped after a successful execution. If `PREPARE` and `DESCRIBE` \(if any\) are successful but the statement cannot be executed, a warning ***SQLCODE 111, SQLSTATE 01W08*** is set, and the statement is not dropped.

    The WITH EXECUTE clause might improve performance, as it decrease the required client/server communication.

  WITH VARIABLE RESULT
 :   Describes procedures that may have more than one result set, with different numbers or types of columns. If the WITH VARIABLE RESULT clause is used, the database server sets the SQLCOUNT value after the describe to one of these values:

    -   0 – the result set may change: the procedure call should be described again following each `OPEN` statement.
    -   1 – the result set is fixed. No reßdescribing is required.

 

<a name="loioa621eea184f210159e6ef52c2216ba0b__IQ_Usage"/>

## Remarks

The `PREPARE` statement prepares a SQL statement from the *<statement\>* and associates the prepared statement with *<statement-name\>*.

If a host variable is used for *<statement-name\>*, it must have the type `short int`. There is a typedef for this type in `sqlca.h` called `a_sql_statement_number`. This type is recognized by the SQL preprocessor and can be used in a `DECLARE` section. The host variable is filled in by the database during the `PREPARE` statement and need not be initialized by the programmer.

These statements can be prepared:

-   `ALTER`
-   `CALL`
-   `COMMENT ON`
-   `CREATE`
-   `DELETE`
-   `DROP`
-   `GRANT`
-   `INSERT`
-   `REVOKE`
-   `SELECT`
-   `SET OPTION`

Preparing `COMMIT`, `PREPARE TO COMMIT`, and `ROLLBACK` statements is still supported for compatibility. However, perform all transaction management operations with static Embedded SQL, because certain application environments may require it. Also, other Embedded SQL systems do not support dynamic transaction management operations.

> ### Note:  
> Make sure that you DROP the statement after use. If you do not, then the memory associated with the statement is not reclaimed.



<a name="loioa621eea184f210159e6ef52c2216ba0b__IQ_Permissions"/>

## Privileges

None



<a name="loioa621eea184f210159e6ef52c2216ba0b__IQ_Side_Effects"/>

## Side Effects

Any statement previously prepared with the same name is lost.



<a name="loioa621eea184f210159e6ef52c2216ba0b__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa621eea184f210159e6ef52c2216ba0b__IQ_Examples"/>

## Examples

The following example prepares a simple query:

```
EXEC SQL PREPARE employee_statement FROM
'SELECT Surname FROM Employees';
```

**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[DESCRIBE Statement \[ESQL\] for Data Lake Relational Engine](describe-statement-esql-for-data-lake-relational-engine-a61bb2c.md "Gets information about the host variables required to store data retrieved from the database or host variables used to pass data to the database.")

[DROP Statement for Data Lake Relational Engine](drop-statement-for-data-lake-relational-engine-a61c216.md "Removes objects from the database.")

[EXECUTE Statement \[ESQL\] for Data Lake Relational Engine](execute-statement-esql-for-data-lake-relational-engine-a774406.md "Executes a SQL statement.")

[OPEN Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](open-statement-esql-sp-for-data-lake-relational-engine-a6215ad.md "Opens a previously declared cursor to access information from the database.")

