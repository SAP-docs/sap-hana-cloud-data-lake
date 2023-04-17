<!-- loio58c58a93e1de4d409e3776c4b92790e1 -->

# DROP FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes user-defined function from the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP FUNCTION [ IF EXISTS ] [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <function-name> (varname] 
```



<a name="loio58c58a93e1de4d409e3776c4b92790e1__IQ_Parameters"/>

## Parameters

 IF EXISTS
 :   Prevents the return of an error if the specified function does not exist.

 

<a name="loio58c58a93e1de4d409e3776c4b92790e1__IQ_Permissions"/>

## Privileges

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:

 Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:
 :   You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

  Connected directly to data lake Relational Engine as a data lake Relational Engine user:
 :   -   Requires one of:
    -   You own the procedure.
    -   DROP ANY PROCEDURE system privilege
    -   DROP ANY OBJECT system privilege
    -   DROP object-level privilege on the procedure
    -   DROP object-level privilege on the schema containing the procedure if the schema is owned by another user.


 

<a name="loio58c58a93e1de4d409e3776c4b92790e1__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Closes all cursors for the current connection.



<a name="loio58c58a93e1de4d409e3776c4b92790e1__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant



<a name="loio58c58a93e1de4d409e3776c4b92790e1__IQ_Examples"/>

## Examples

The following example drops the `Departments` function from the database:

```
DROP FUNCTION Departments
```

**Related Information**  


[CREATE FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-function-statement-for-data-lake-relational-engine-sap-hana-db-managed-abddfd6.md "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.")

[ALTER FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-function-statement-for-data-lake-relational-engine-sap-hana-db-managed-3d7a54b.md "Modifies an existing function. Include the entire modified function in the ALTER FUNCTION statement.")

[DROP Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a61c216b84f21015baa181c153419bbb.html "Removes objects from the database.") :arrow_upper_right:

