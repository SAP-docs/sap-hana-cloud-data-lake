<!-- loioa61c216b84f21015baa181c153419bbb -->

# DROP Statement for Data Lake Relational Engine

Removes objects from the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP
   { DATATYPE [ IF EXISTS ]
   | DOMAIN } <datatype-name>
   | MESSAGE <message-number>
   | EVENT [ IF EXISTS ] <event-name>
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) INDEX [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <table-name> (varname].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <index-name> (varname] (span]
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) TABLE [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <table-name> (varname] (span]
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) VIEW [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <view-name> (varname] (span]
   | [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) MATERIALIZED VIEW [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <mat-view-name> (varname] (span][/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) 
   | SCHEMA [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema_name> (varname] [ RESTRICT ] (span]
   | PROCEDURE [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <procedure-name> (varname]
   | FUNCTION [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) { [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <owner> (varname] | [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] } (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <function-name> (varname]  }
```



<a name="loioa61c216b84f21015baa181c153419bbb__IQ_Parameters"/>

## Parameters

 IF EXISTS
 :   Use if you do not want an error returned when the DROP statement attempts to remove a database object that does not exist.

  SCHEMA
 :   If you drop a schema, then any schema synonym that references it is also dropped. You cannot drop a user if they own a schema.

  RESTRICT
 :   RESTRICT drops the schema, but only when there are no objects in it. If there are still objects in the schema, then an error is returned.

  INDEX
 :   DROP INDEX deletes any explicitly created index. It deletes an implicitly created index only if there are no unique or foreign-key constraints or associated primary key.

    DROP INDEX is prevented whenever the statement affects a table that is currently being used by another connection.

    For a nonunique HG index, DROP INDEX fails if an associated unenforced foreign key exists.

    > ### Caution:  
    > Do not delete views owned by the DBO user. Deleting such views or changing them into tables might cause problems.

  TABLE
 :   DROP TABLE is prevented whenever the statement affects a table that is currently being used by another connection or if the primary table has foreign-key constraints associated with it, including unenforced foreign-key constraints. It is also prevented if the table has an IDENTITY column and IDENTITY\_INSERT is set to that table. To drop the table, you must clear IDENTITY\_INSERT, that is, set IDENTITY\_INSERT to ' ' \(an empty string\), or set to another table name.

    A foreign key can have either a nonunique single or a multicolumn HG index. A primary key may have unique single or multicolumn HG indexes. You cannot drop the HG index implicitly created for an existing foreign key, primary key, and unique constraint.

    The four initial dbspaces are SYSTEM, IQ\_SYSTEM\_MAIN, IQ\_SYSTEM\_TEMP, and IQ\_SYSTEM\_MSG. You cannot drop these initial dbspaces, but you may drop dbspaces from the IQ main store or catalog store, which may contain multiple dbspaces, as long as at least one dbspace remains with readwrite mode.

  PROCEDURE
 :   DROP PROCEDURE is prevented when the procedure is in use by another connection.

  DATATYPE
 :   DROP DATATYPE is prevented if the data type is used in a table. You must change data types on all columns defined on the user-defined data type to drop the data type. It is recommended that you use DROP DOMAIN rather than DROP DATATYPE, as DROP DOMAIN is the syntax used in the ANSI/ISO SQL3 draft.

 

<a name="loioa61c216b84f21015baa181c153419bbb__IQ_Usage"/>

## Remarks

DROP removes the definition of the indicated database structure. If the structure is a table, all data in the table is automatically deleted as part of the dropping process. Also, all indexes and keys for the table are dropped by DROP TABLE.

Global temporary tables cannot be dropped unless all users that have referenced the temporary table have disconnected.



<a name="loioa61c216b84f21015baa181c153419bbb__drop_privileges1"/>

## Privileges



### 

The privilege required varies by clause.


<table>
<tr>
<th valign="top">

Clause



</th>
<th valign="top">

Privilege Required



</th>
</tr>
<tr>
<td valign="top">

DOMAIN and DATATYPE



</td>
<td valign="top">

-   Requires one of:
    -   You own the object
    -   DROP DATATYPE system privilege




</td>
</tr>
<tr>
<td valign="top">

EVENT



</td>
<td valign="top">

-   Self-owned events require:
    -   MANAGE EVENT system privilege

-   Events owned by others require one of:
    -   MANAGE ANY EVENT system privilege
    -   DROP ANY OBJECT system privilege




</td>
</tr>
<tr>
<td valign="top">

FUNCTION



</td>
<td valign="top">

-   Requires one of:
    -   You own the procedure.
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.




</td>
</tr>
<tr>
<td valign="top">

INDEX



</td>
<td valign="top">

-   Requires one of:
    -   You own the underlying table of the index.
    -   DROP ANY INDEX system privilege
    -   DROP ANY OBJECT system privilege
    -   REFERENCES or DROP object-level privilege on the underlying table of the index.
    -   REFERENCE or DROP object-level privilege on the schema containing the underlying table of the index if the schema is owned by another user.




</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

You own the message.



</td>
</tr>
<tr>
<td valign="top">

MATERIALIZED VIEW



</td>
<td valign="top">

Requires one of:

-   You own the materialized view.
-   DROP ANY MATERIALIZED VIEW system privilege
-   DROP ANY OBJECT system privilege.
-   DROP object-level privilege on the schema containing the materialized view if the schema is owned by another user.



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE



</td>
<td valign="top">

-   Requires one of:
    -   You own the procedure
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.




</td>
</tr>
<tr>
<td valign="top">

SCHEMA



</td>
<td valign="top">

Requires one of:

-   You own the schema.
-   DROP ANY DATABASE system privilege
-   DROP ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

TABLES



</td>
<td valign="top">

Requires one of:

-   You own the table.
-   DROP ANY TABLE system privilege
-   DROP ANY OBJECT system privilege
-   DROP object-level privilege on the table.
-   DROP object-level privilege on the schema containing the table if the schema is owned by another user.



</td>
</tr>
<tr>
<td valign="top">

VIEW



</td>
<td valign="top">

Requires one of:

-   You own the view.
-   DROP ANY VIEW system privilege
-   DROP ANY OBJECT system privilege.
-   DROP object-level privilege on the schema containing the view if the schema is owned by another user.



</td>
</tr>
</table>

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa61c216b84f21015baa181c153419bbb__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql. DROP TABLE and DROP INDEX close all cursors for the current connection.
-   Local temporary tables are an exception; no commit is performed when one is dropped.



<a name="loioa61c216b84f21015baa181c153419bbb__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa61c216b84f21015baa181c153419bbb__IQ_Examples"/>

## Examples

-   ```
DROP TABLE Departments
```

-   The following example drop the emp\_dept view from the database:The following example drop the Departments table from the database:

    ```
    DROP VIEW emp_dept
    ```

-   The following example drop the myDAS main cache from the node you are connected to:

    ```
    DROP DBSPACE myDAS
    ```


**Related Information**  


[ALTER TABLE Statement for Data Lake Relational Engine](alter-table-statement-for-data-lake-relational-engine-39f1ec0.md "Modifies a table definition.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[CREATE VIEW Statement for Data Lake Relational Engine](create-view-statement-for-data-lake-relational-engine-a61a051.md "Creates a view on the database. Views are used to give a different perspective on the data even though it is not stored that way.")

[CREATE DOMAIN Statementfor Data Lake Relational Engine](create-domain-statementfor-data-lake-relational-engine-a616d8e.md "Creates a user-defined data type in the database.")

[CREATE EVENT Statement for Data Lake Relational Engine](create-event-statement-for-data-lake-relational-engine-a617091.md "Defines an event and its associated handler for automating predefined actions. Also defines scheduled actions.")

[CREATE FUNCTION Statement for Data Lake Relational Engine](create-function-statement-for-data-lake-relational-engine-a61796c.md "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.")

[CREATE INDEX Statement for Data Lake Relational Engine](create-index-statement-for-data-lake-relational-engine-a617ca4.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[CREATE MESSAGE Statement \[T-SQL\] for Data Lake Relational Engine](create-message-statement-t-sql-for-data-lake-relational-engine-a61829d.md "Adds a user-defined message to the SYSUSERMESSAGES system table for use by PRINT and RAISERROR statements.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine](create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

