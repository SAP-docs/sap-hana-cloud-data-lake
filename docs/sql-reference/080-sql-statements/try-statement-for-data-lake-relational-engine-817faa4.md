<!-- loio817faa4f6ce210149928aea666aaa42d -->

# TRY Statement for Data Lake Relational Engine

Implements error handling for compound statements \(if an error occurs in the TRY block, it passes control to another group of statements that is enclosed in a CATCH block\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
[ <statement-label> ::= ]
   BEGIN TRY
      [ <local-declaration;> ... ]
      [ <statement-list> ]
   END TRY
   BEGIN CATCH
      [ <statement-list> ]
   END CATCH
```

```
<local-declaration> ::=
   { <variable-declaration>
   | <cursor-declaration>
   | <exception-declaration>
   | <temporary-table-declaration> }
```

```
 : a valid DECLARE statement
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl class="glossary">
<dt><b>

 *<statement-label\>* 

</b></dt>
<dd>

When an ending *<statement-label\>* is specified, it must match the beginning *<statement-label\>*. The LEAVE statement can be used to resume execution at the first statement after the compound statement. The compound statement that is the body of a procedure or trigger has an implicit label that is the same as the name of the procedure or trigger.



</dd><dt><b>

 *<local-declaration\>* 

</b></dt>
<dd>

Immediately following the BEGIN TRY, a compound statement can have local declarations for objects that only exist within the compound statement. A compound statement can have a local declaration for a variable, a cursor, a temporary table, or an exception. Local declarations can be referenced by any statement in that compound statement, or in any compound statement nested within it. Local declarations of the compound statement are visible to the exception handler for the statement. Local declarations are not visible to other procedures that are called from within a compound statement.



</dd><dt><b>

 *<variable-declaration\>* 

</b></dt>
<dd>

A valid DECLARE statement.



</dd><dt><b>

 *<exception-declaration\>* 

</b></dt>
<dd>

A valid DECLARE statement.



</dd><dt><b>

 *<cursor-declaration\>* 

</b></dt>
<dd>

A valid DECLARE CURSOR statement.



</dd><dt><b>

 *<temporary-table-declaration\>* 

</b></dt>
<dd>

A valid DECLARE LOCAL TEMPORARY TABLE statement.



</dd>
</dl>



## Remarks

The CATCH block is the error handler for the TRY statement.

TRY...CATCH statements can be nested and used anywhere that a BEGIN...END statement can be used. Statements within the TRY block ignore the on\_tsql\_error and continue\_after\_raiserror database options, as well as the ON EXCEPTION RESUME clause of the CREATE PROCEDURE statement. TRY...CATCH statements are not atomic.

If no errors occur in the TRY block, the CATCH block is skipped and control passes to the statement following the CATCH block or the caller if no such statement exists. If an error occurs in one of the statements in the TRY block, control passes to the first statement in the CATCH block. Once the CATCH block completes, control passes to the statement following the CATCH block or the caller if no such statement exists. The effect of statements that precede a statement that generates an error is not reverted unless the exception handler generates an error and is nested within an atomic block or an explicit ROLLBACK statement is called. In this case, all statements within the atomic transaction block are reverted.

Errors in the CATCH block are handled according to the connection and procedure settings unless the statements generating them are enclosed in additional TRY...CATCH statements.



## Privileges

None.



## Side Effects

None.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



These examples use the following table:

```
CREATE TABLE t( col1 DOUBLE );
```

Executing the following compound statement inserts value 6 into table t:

```
BEGIN TRY
    DECLARE val INT;

    SET val = 0;

    INSERT INTO t VALUES( 1 / val );
    -- This statement will not be executed
    INSERT INTO t VALUES( val );
END TRY
BEGIN CATCH
    SET val = 6;
    INSERT INTO t VALUES( val );
END CATCH;
```

Executing the following procedure by using `CALL proc1(10);` inserts the following values into the table t:


<table>
<tr>
<td valign="top">

\-10



</td>
</tr>
<tr>
<td valign="top">

10



</td>
</tr>
</table>

```
CREATE PROCEDURE DBA.proc1( v INTEGER )
BEGIN TRY
    DECLARE local_val INTEGER = 0;

    INSERT INTO t VALUES(-v);

    SET local_val = v / local_val;
    -- This statement will not be executed
    MESSAGE 'The value is ', v;
END TRY
BEGIN CATCH
    INSERT INTO t VALUES(v);
END CATCH;
```

