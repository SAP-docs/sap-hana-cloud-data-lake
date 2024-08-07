<!-- loio3d7a54b993a74668b60ab048e299fbec -->

# ALTER FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Modifies an existing function. Include the entire modified function in the ALTER FUNCTION statement.



<a name="loio3d7a54b993a74668b60ab048e299fbec__section_jzt_bmj_g4b"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Change the definition of a function

</b></dt>
<dd>

```
ALTER FUNCTION [ <schema-name>.]<function-name> 
   ( [ IN <parameter-name> <data-type> [ DEFAULT <expression> ], … ] )
   RETURNS <data-type> 
   [ SQL SECURITY { INVOKER | DEFINER } ]
   [ ON EXCEPTION RESUME ]
   [ [ NOT ] DETERMINISTIC ]
   { <compound-statement> 
      | AS <sql-statement> <sql-statement>... }

```



</dd><dt><b>

Obfuscate a function definition

</b></dt>
<dd>

```
ALTER FUNCTION [ .]<function-name> 
SET HIDDEN
```



</dd><dt><b>

Recompile a function

</b></dt>
<dd>

```
ALTER FUNCTION [ .]<function-name>
RECOMPILE
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio3d7a54b993a74668b60ab048e299fbec__section_jnd_wqk_sqb"/>

## Parameters


<dl>
<dt><b>

SQL SECURITY

</b></dt>
<dd>

Defines whether the function is executed as the INVOKER, the user who is calling the function, or as the DEFINER, the user who owns the function. The default is DEFINER.

When INVOKER is specified, more memory is used because annotation must be done for each user that calls the procedure. Also, name resolution is done as the invoker as well. Therefore, take care to qualify all object names \(tables, procedures, and so on\) with their appropriate owner.



</dd><dt><b>

*<data-type\>*

</b></dt>
<dd>

The data type of the parameter. Set the data type explicitly, or specify the %TYPE or %ROWTYPE attribute to set the data type to the data type of another object in the database. Use %TYPE to set it to the data type of a column in a table or view. Use %ROWTYPE to set the data type to a composite data type derived from a row in a table or view. LONG BINARY and LONG VARCHAR are not permitted as return-value data types.



</dd><dt><b>

*<compound-statement\>*

</b></dt>
<dd>

A set of SQL statements bracketed by BEGIN and END, and separated by semicolons. See *BEGIN … END Statement*.



</dd><dt><b>

ON EXCEPTION RESUME

</b></dt>
<dd>

Uses Transact-SQL-like error handling. See *CREATE PROCEDURE Statement*.



</dd><dt><b>

\[NOT\] DETERMINISTIC

</b></dt>
<dd>

Function is re-evaluated each time it is called in a query. The results of functions not specified in this manner may be cached for better performance, and re-used each time the function is called with the same parameters during query evaluation.

Functions that have side effects, such as modifying the underlying data, should be declared as NOT DETERMINISTIC. For example, a function that generates primary key values and is used in an INSERT … SELECT statement should be declared NOT DETERMINISTIC:

```
CREATE FUNCTION keygen( increment INTEGER ) 
RETURNS INTEGER 
NOT DETERMINISTIC 
BEGIN   
  DECLARE keyval INTEGER;  
  UPDATE counter SET x = x + increment;  
  SELECT counter.x INTO keyval FROM counter;   
  RETURN keyval 
END 
INSERT INTO new_table 
SELECT keygen(1), ... 
FROM old_table;
```

Functions may be declared as DETERMINISTIC if they always return the same value for given input parameters. All user-defined functions are treated as deterministic unless they are declared NOT DETERMINISTIC. Deterministic functions return a consistent result for the same parameters and are free of side effects. That is, the database server assumes that two successive calls to the same function with the same parameters will return the same result without unwanted side-effects on the semantics of the query.



</dd><dt><b>

SET HIDDEN

</b></dt>
<dd>

Scrambles the definition of the associated function and causes it to become unreadable. The function can be unloaded and reloaded into other databases.

> ### Caution:  
> The SET HIDDEN clause setting is irreversible. If you need the original source again, you must maintain it outside the database.



</dd><dt><b>

RECOMPILE

</b></dt>
<dd>

Recompiles a user-defined function. When you recompile a function, the definition stored in the catalog is re-parsed and the syntax is verified. The preserved source for a function is not changed by recompiling. When you recompile a function, the definitions scrambled by the SET HIDDEN clause remain scrambled and unreadable.



</dd>
</dl>



<a name="loio3d7a54b993a74668b60ab048e299fbec__section_hsf_zqk_sqb"/>

## Remarks

You must include the entire new function in the ALTER FUNCTION statement.

Existing privileges on the function remain unmodified. Conversely, if you execute DROP FUNCTION followed by CREATE FUNCTION, execute privileges are reassigned.

For **required** parameters that accept variable names, an error is returned if one of the following conditions is true:

-   The variable does not exist
-   The contents of the variable are NULL
-   The variable exceeds the length allowed by the parameter
-   The data type of the variable does not match that required by the parameter



<a name="loio3d7a54b993a74668b60ab048e299fbec__section_df1_11q_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


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

Requires one of:

-   You own the function
-   ALTER ANY PROCEDURE system privilege
-   ALTER ANY OBJECT system privilege
-   ALTER object-level privilege on the schema containing the function if the schema is owned by another user.

For information on using a function created when connected as a data lake Relational Engine user, see [User-Defined Functions in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/abea6df6284d46c8b2265c477be1f704.html "User-defined functions are a class of procedures that return a single value to the calling environment.") :arrow_upper_right:.



</dd>
</dl>



<a name="loio3d7a54b993a74668b60ab048e299fbec__section_m21_crk_sqb"/>

## Side Effects

Automatic commit



<a name="loio3d7a54b993a74668b60ab048e299fbec__section_eqd_drk_sqb"/>

## Standards

SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[CREATE FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-function-statement-for-data-lake-relational-engine-sap-hana-db-managed-abddfd6.md "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.")

[DROP FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-function-statement-for-data-lake-relational-engine-sap-hana-db-managed-58c58a9.md "Removes a user-defined function from the database.")

[ALTER FUNCTION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a61280af84f21015a184bc25f16886f8.html "Modifies an existing function. Include the entire modified function in the ALTER FUNCTION statement.") :arrow_upper_right:

