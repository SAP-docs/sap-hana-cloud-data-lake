<!-- loioa61dfe2b84f210159a53c67a84c3c01b -->

# EXECUTE IMMEDIATE Statement \[ESQL\] \[SP\] for Data Lake Relational Engine

Extends the range of statements that can be executed from within procedures. It lets you execute dynamically prepared statements, such as statements that are constructed using the parameters passed in to a procedure.



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
EXECUTE IMMEDIATE 
   [ { WITH QUOTES { ON | OFF }
     | WITH ESCAPES { ON | OFF } 
     | WITH RESULT SET { ON | OFF } }
   ] <string-expression>
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
EXECUTE ( <string-expression> )
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

WITH QUOTES \[ON\]

</b></dt>
<dd>

Any double quotes in the string expression are assumed to delimit an identifier. When not specified, the treatment of double quotes in the string expression depends on the current setting of the `QUOTED_IDENTIFIER` database option.

`WITH QUOTES` is useful when an object name that is passed into the stored procedure is used to construct the statement that is to be executed, but the name might require double quotes and the procedure might be called when `QUOTED_IDENTIFIER` is set to OFF.

See *QUOTED\_IDENTIFIER Option \[TSQL\]*.



</dd><dt><b>

WITH ESCAPES

</b></dt>
<dd>

Causes any escape sequences \(such as \\n, \\x, or \\\\\) in the string expression to be ignored. For example, two consecutive backslashes remain as two backslashes, rather than being converted to a single backslash. The default setting is ON.

You can use `WITH ESCAPES OFF` for easier execution of dynamically constructed statements referencing file names that contain backslashes.



</dd><dt><b>

*<string-expression\>*

</b></dt>
<dd>

In some contexts, escape sequences in the *<string-expression\>* are transformed before `EXECUTE IMMEDIATE` is executed. For example, compound statements are parsed before being executed, and escape sequences are transformed during this parsing, regardless of the WITH ESCAPES setting. In these contexts, `WITH ESCAPES OFF` prevents further translations from occurring. For example:

```
BEGIN
DECLARE String1 LONG VARCHAR;
DECLARE String2 LONG VARCHAR;
EXECUTE IMMEDIATE 
 'SET String1 = ''One backslash: \\\\ '''; 
 EXECUTE IMMEDIATE WITH ESCAPES OFF 
 'SET String2 = ''Two backslashes: \\\\ ''';  
 SELECT String1, String2 
END
```



</dd><dt><b>

WITH RESULT SET

</b></dt>
<dd>

When specified with ON, the `EXECUTE IMMEDIATE` statement returns a result set. With this clause, the containing procedure is marked as returning a result set. If you do not include this clause, an error is reported when the procedure is called if the statement does not produce a result set.

> ### Note:  
> The default option is OFF, meaning that no result set is produced when the statement is executed.



</dd>
</dl>



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__IQ_Usage"/>

## Remarks

Literal strings in the statement must be enclosed in single quotes, and must differ from any existing statement name in a `PREPARE` or `EXECUTE IMMEDIATE` statement. The statement must be on a single line.

Only global variables can be referenced in a statement executed by `EXECUTE IMMEDIATE`.

Only syntax 2 can be used inside Transact-SQL stored procedures.

The statement is executed with the permissions of the owner of the procedure, not with the permissions of the user who calls the procedure.



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__IQ_Permissions"/>

## Privileges

None



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__IQ_Side_Effects"/>

## Side Effects

None. However, if the statement is a data definition statement with an automatic commit as a side effect, then that commit does take place.



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61dfe2b84f210159a53c67a84c3c01b__IQ_Examples"/>

## Examples

The following example creates a table, where the table name is supplied as a parameter to the procedure. The full `EXECUTE IMMEDIATE` statement must be on a single line:

```
CREATE PROCEDURE CreateTableProc(
            IN tablename char(30)
            )
BEGIN
 EXECUTE IMMEDIATE 'CREATE TABLE ' || tablename ||
' ( column1 INT PRIMARY KEY)'
END;
```

Call the procedure and create table `mytable`:

```
CALL CreateTableProc( 'mytable' );
```

**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine](create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

[QUOTED\_IDENTIFIER Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/quoted-identifier-option-tsql-for-data-lake-relational-engine-a651dd4.md "Controls the interpretation of strings that are enclosed in double quotes.")

