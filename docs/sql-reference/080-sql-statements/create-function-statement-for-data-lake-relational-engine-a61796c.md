<!-- loioa61796cb84f2101594a2b0b5a6993b95 -->

# CREATE FUNCTION Statement for Data Lake Relational Engine

Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.



<a name="loioa61796cb84f2101594a2b0b5a6993b95__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] [ TEMPORARY ] FUNCTION [ { <owner> | <schema-name> }.]<function-name>
   ( [ IN <parameter-name> <data-type> [ DEFAULT <expression> ], … ] )
   RETURNS <data-type> 
   [ SQL SECURITY { INVOKER | DEFINER } ]
   [ ON EXCEPTION RESUME ]
   [ [ NOT ] DETERMINISTIC ]
   { <compound-statement> 
      | AS <sql-statement> <sql-statement>... };
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61796cb84f2101594a2b0b5a6993b95__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

CREATE \[ OR REPLACE \]

</b></dt>
<dd>

Parameter names must conform to the rules for database identifiers. They must have a valid SQL data type and be prefixed by the keyword IN, signifying that the argument is an expression that provides a value to the function.

The CREATE clause creates a new function, while the OR REPLACE clause replaces an existing function with the same name. When a function is replaced, the definition of the function is changed but the existing permissions are preserved. You cannot use the OR REPLACE clause with temporary functions.



</dd><dt><b>

TEMPORARY

</b></dt>
<dd>

The function is visible only by the connection that created it, and that it is automatically dropped when the connection is dropped. Temporary functions can also be explicitly dropped. You cannot perform ALTER, GRANT, or REVOKE operations on them, and unlike other functions, temporary functions are not recorded in the catalog or transaction log.

Temporary functions execute with the permissions of their creator \(current user\), and can only be owned by their creator. Therefore, do not specify owner when creating a temporary function. They can be created and dropped when connected to a read-only database.



</dd><dt><b>

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



</dd>
</dl>



<a name="loioa61796cb84f2101594a2b0b5a6993b95__create_funct_remarks1"/>

## Remarks

To modify a user-defined function, or to hide the contents of a function by scrambling its definition, use the ALTER FUNCTION statement.

When functions are executed, not all parameters need to be specified. If a default value is provided in the CREATE FUNCTION statement, then missing parameters are assigned the default values. If an argument is not provided by the caller and no default is set, then an error is given.



### Required Parameters

For required parameters that accept variable names, an error is returned if one of the following conditions is true:

-   The variable does not exist
-   The contents of the variable are NULL
-   The variable exceeds the length allowed by the parameter
-   The data type of the variable does not match that required by the parameter



<a name="loioa61796cb84f2101594a2b0b5a6993b95__create_funct_privileges1"/>

## Privileges



### 

Function ownership determines the privilege required.

-   To create a self owned function requires the CREATE PROCEDURE system privilege.
-   To create a function owned by another user requires one of:
    -   CREATE ANY PROCEDURE system privilege.
    -   CREATE ANY OBJECT system privilege.
    -   CREATE ANY object-level privilege on the schema if the function is in a schema owned by another user.

-   To replace an existing function requires one of:
    -   You own the function.
    -   DROP ANY PROCEURE or DROP ANY OBJECT along with CREATE ANY PROCEDURE or CREATE ANY OBJECT
    -   If the function is in a schema owned by another user, then you need one of:
        -   DROP and CREATE ANY object-level privilege on the schema
        -   ALTER object-level privilege on the schema.



See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61796cb84f2101594a2b0b5a6993b95__create_funct_sideeffects1"/>

## Side Effects

Automatic commit



<a name="loioa61796cb84f2101594a2b0b5a6993b95__create_funct_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa61796cb84f2101594a2b0b5a6993b95__create_funct_examples1"/>

## Examples

-   The following example concatenates a `firstname` string and a `lastname` string:

    ```
    CREATE OR REPLACE FUNCTION fullname (
      firstname CHAR(30),
      lastname CHAR(30) )
    RETURNS CHAR(61)
    BEGIN
      DECLARE name CHAR(61);
      SET name = firstname || ' ' || lastname;
      RETURN (name);
    END;
    ```

-   This example illustrates the use of the `fullname` function.

    -   Return a full name from two supplied strings:

        ```
        SELECT fullname ('joe','smith');
        ```


        <table>
        <tr>
        <th valign="top">

        fullname\('joe', 'smith'\)
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        joe smith
        
        </td>
        </tr>
        </table>
        
    -   List the names of all employees:

        ```
        SELECT fullname (givenname, surname)
        FROM Employees;
        ```


        <table>
        <tr>
        <th valign="top">

        fullname \(givenname, surname\)
        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
        Fran Whitney
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Matthew Cobb
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Philip Chin
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Julie Jordan
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Robert Breault
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        ...
        
        </td>
        </tr>
        </table>
        

-   The following example uses Transact-SQL syntax:

    ```
    CREATE FUNCTION DoubleIt ( @Input INT )
    RETURNS INT 
    AS 
    DECLARE @Result INT  
    SELECT @Result = @Input * 2 
    RETURN @Result;
    ```

    The statement `SELECT DoubleIt( 5 )` returns a value of `10`.


**Related Information**  


[ALTER FUNCTION Statement for Data Lake Relational Engine](alter-function-statement-for-data-lake-relational-engine-a61280a.md "Modifies an existing function. Include the entire modified function in the ALTER FUNCTION statement.")

[DROP FUNCTION Statement for Data Lake Relational Engine](drop-function-statement-for-data-lake-relational-engine-d42de2d.md "Removes a user-defined function from the database.")

[BEGIN … END Statement for Data Lake Relational Engine](begin-end-statement-for-data-lake-relational-engine-a6142de.md "Groups SQL statements together.")

[INSERT Statement for Data Lake Relational Engine](insert-statement-for-data-lake-relational-engine-a61fdef.md "Inserts a single row or a selection of rows, from elsewhere in the current database, into the table. This command can also insert a selection of rows from another database into the table.")

[RETURN Statement for Data Lake Relational Engine](return-statement-for-data-lake-relational-engine-a623cb4.md "Exits a function or procedure unconditionally, optionally providing a return value. Statements following RETURN are not executed.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE FUNCTION Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/abddfd62461747b08416521922da3577.html "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.") :arrow_upper_right:

