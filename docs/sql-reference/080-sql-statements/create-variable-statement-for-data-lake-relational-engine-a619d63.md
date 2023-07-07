<!-- loioa619d63284f21015b33fddf934b664e3 -->

# CREATE VARIABLE Statement for Data Lake Relational Engine

Creates data type or a connection- or database-scope variable.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1 – Creates a Connection-Scope Variable

</b></dt>
<dd>

```
<identifier> <data-type> 
   [ { = | DEFAULT } CREATE [ OR REPLACE ] VARIABLE <initial-value> ]
```

```
<initial-value> ::= <expression>
```



</dd><dt><b>

Syntax 2 – Creates a Data Type or Database-Scope Variable

</b></dt>
<dd>

```
CREATE [ OR REPLACE ] DATABASE VARIABLE [ IF NOT EXISTS ] 
    [ <owner>.]<identifier> <data-type> [ { = | DEFAULT } <initial-value> ]
```



</dd>
</dl>

```
<initial-value> ::=
   { <special-value> 
   | <string> | [ - ] <number> 
   | ( <constant-expression> ) 
   | <built-in-function> ( <constant-expression> ) 
   | NULL }
```

```
<special-value> ::=
   { CURRENT 
     { DATABASE 
     | DATE 
     | PUBLISHER 
     | TIME 
     | TIMESTAMP 
     | USER 
     | UTC TIMESTAMP }
   | USER }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa619d63284f21015b33fddf934b664e3__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

CREATE \[OR REPLACESpecifying the OR REPLACE clause drops the named variable if it already exists and re-creates it with the new definition. OR REPLACE only replaces the value of the variable if the data type of the current and new value are the same.

Do not use this clause with the IF NOT EXISTS clause.



</dd><dt><b>

*<owner\>*

</b></dt>
<dd>

This parameter applies only to database-scope variables. Specify a valid user ID or role, or PUBLIC to set ownership of the variable. If set to a user, only that user can use the database variable. If set to a role, users who have that role are able to use the database variable. If set to PUBLIC, all users are able to use the variable.

If *<owner\>* is not specified, it is set to the user executing the CREATE VARIABLE statement.



</dd><dt><b>

*<identifier\>*

</b></dt>
<dd>

A valid identifier for the variable.



</dd><dt><b>

*<data-type\>*

</b></dt>
<dd>

The data type for the variable. Set the data type explicitly, or use the %TYPE or %ROWTYPE attribute to set the data type to the data type of another object in the database. Use %TYPE to set it to the data type of a variable or a column in a table or view. Use %ROWTYPE to set the data type to a composite data type derived from a row in a cursor, table, or view.

%ROWTYPE and TABLE REF is not supported as data types for database-scope variables.



</dd><dt><b>

IF NOT EXISTS

</b></dt>
<dd>

Specify this clause to allow the statement to complete without returning an error if a database-scope variable with the same name already exists. This parameter is only for use when creating owned database-scope variables.

Do not use this clause with the OR REPLACE clause.



</dd><dt><b>

= | DEFAULT

</b></dt>
<dd>

The default value for the variable. For database-scope variables, this is also the initial value after the database is restarted.

*<initial-value\>* must match the data type defined by *<data-type\>*. If you do not specify an *<initial-value\>*, then the variable contains the NULL value until a different value is assigned, for example by using a SET statement, a SELECT ... INTO statement, or in an UPDATE statement. If *<initial-value\>* is set by using an expression, then the expression is evaluated at creation time and the resulting constant is stored \(not the expression\).



</dd>
</dl>



<a name="loioa619d63284f21015b33fddf934b664e3__IQ_Usage"/>

## Remarks

A variable can be used in a SQL expression anywhere a column name is allowed. If a column name exists with the same name as the variable, the variable value is used. Name resolution is performed as follows:

-   Match any aliases specified in the query's SELECT list.
-   Match column names for any referenced tables.
-   Assume the name is a variable.

Variables belong to the current connection, and disappear when you disconnect from the database, or when you use the `DROP VARIABLE` statement. Variables are not visible to other connections. `COMMIT` or `ROLLBACK` statements do not affect variables.

Variables created with the `CREATE VARIABLE` statement persist for a connection even when the statement is issued within a `(BEGIN...END)` statement. You must use `DECLARE` to create variables that only persist within a `(BEGIN...END)` statement, for example, within stored procedures.

Variables are useful for creating large text or binary objects for `INSERT` or `UPDATE` statements from Embedded SQL programs.

Use the CREATE VARIABLE syntax to create a connection-scope variable that is available in the context of the connection.

Use the OR REPLACE clause as an alternative to the VAREXISTS function in SQL scripts.

If you specify a variable name for *<initial-value\>*, then the variable must already be initialized in the database.

Local variables in procedures and triggers are declared within a compound statement.



<a name="loioa619d63284f21015b33fddf934b664e3__IQ_Permissions"/>

## Privileges

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.


<table>
<tr>
<th valign="top">

Scope



</th>
<th valign="top">

Privilege Required



</th>
</tr>
<tr>
<td valign="top">

Connection-scope variables



</td>
<td valign="top">

No privileges are required to create or replace a connection-scope variable.



</td>
</tr>
<tr>
<td valign="top">

Database-scope variables



</td>
<td valign="top">

-   To create or replace a self-owned database-scope variable requires the MANAGE ANY DATABASE VARIABLE system privilege.
-   To create or replace a database-scope variable owned by another user or by PUBLIC requires the MANAGE ANY DATABASE VARIABLE system privilege.



</td>
</tr>
</table>



<a name="loioa619d63284f21015b33fddf934b664e3__IQ_Side_Effects"/>

## Side Effects

-   Connection-scope variables – there are no side effects associated with creating a connection-scope variable.
-   Database-scope variables – creating and replacing a database-scope variable causes an automatic commit.



<a name="loioa619d63284f21015b33fddf934b664e3__IQ_Standards"/>

## Standards

SQL – not in the ISO/ANSI SQL standard



<a name="loioa619d63284f21015b33fddf934b664e3__IQ_Examples"/>

## Examples

-   The following example creates \(or updates\) a database-scope variable called site\_name of type VARCHAR\(50\).

    ```
    CREATE OR REPLACE DATABASE VARIABLE @site_name VARCHAR(50);
    ```

-   The following example creates \(or updates\) a database-scope variable owned by PUBLIC called database\_name of type CHAR\(66\) and sets it to the special value CURRENT DATABASE.

    ```
    CREATE OR REPLACE DATABASE VARIABLE PUBLIC.@database_name CHAR(66) DEFAULT CURRENT DATABASE;
    ```

-   The following example creates a connection-scope variable named first\_name, of data type VARCHAR\(50\).

    ```
    CREATE VARIABLE first_name VARCHAR(50);
    ```

-   The following example creates a connection-scope variable named birthday, of data type DATE.

    ```
    CREATE VARIABLE birthday DATE;
    ```

-   The following example creates a connection-scope variable named v1 as an INT with the initial setting of 5.

    ```
    CREATE VARIABLE v1 INT = 5;
    ```

-   The following example creates a connection-scope variable named v1 and sets its value to 10, regardless of whether the v1 variable already exists.

    ```
    CREATE OR REPLACE VARIABLE v1 INT = 10;
    ```

-   The following example creates a connection-scope variable, ProductID, and uses the %TYPE attribute to set its data type to the data type of the ID column in the Products table:

    ```
    CREATE VARIABLE ProductID Products.ID%TYPE;
    ```

-   The following example creates a connection-scope variable, ItemsForSale, and uses the %ROWTYPE attribute to set its data type to a composite data type comprised of the columns defined for the Products table. It then creates another variable, ItemID, and declares its type to be the data type of the ID column in the ItemsForSale variable:

    ```
    CREATE VARIABLE ItemsForSale Products%ROWTYPE;
    CREATE VARIABLE ItemID ItemsForSale.ID%TYPE;
    ```

-   The following example this code fragment inserts a large text value into the database:

    ```
    EXEC SQL BEGIN DECLARE SECTION;
    char buffer[5000];
    EXEC SQL END DECLARE SECTION;
    EXEC SQL CREATE VARIABLE hold_blob VARCHAR;
    EXEC SQL SET hold_blob = '';
    for(;;) {
    	/* read some data into buffer ... */
    	size = fread( buffer, 1, 5000, fp );
    	if( size <= 0 ) break;
    	/* add data to blob using concatenation
    	Note that concatenation works for binary 
    	data too! */
    	EXEC SQL SET hold_blob = hold_blob || :buffer;
    }
    EXEC SQL INSERT INTO some_table VALUES ( 1, hold_blob );
    EXEC SQL DROP VARIABLE hold_blob;
    ```


**Related Information**  


[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[DECLARE Statement for Data Lake Relational Engine](declare-statement-for-data-lake-relational-engine-a61a929.md "Declares a SQL variable within a compound statement (BEGIN... END).")

[DROP VARIABLE Statement for Data Lake Relational Engine](drop-variable-statement-for-data-lake-relational-engine-816f992.md "Drops a connection-scope SQL variable.")

[SET SQLCA Statement \[ESQL\] for Data Lake Relational Engine](set-sqlca-statement-esql-for-data-lake-relational-engine-a6263c3.md "Tells the SQL preprocessor to use a SQLCA other than the default global sqlca.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

