<!-- loioabddfd62461747b08416521922da3577 -->

# CREATE FUNCTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.



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
CREATE [ OR REPLACE ] [ TEMPORARY ] FUNCTION [ [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <schema-name> (varname] (span].][/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <function-name> (varname]
   [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) ( [ IN [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <parameter-name> (varname] [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <data-type> (varname] [ DEFAULT [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <expression> (varname] ], … ] )
   RETURNS [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <data-type> (varname] 
   [ SQL SECURITY { INVOKER | DEFINER } ]
   [ ON EXCEPTION RESUME ]
   [ [ NOT ] DETERMINISTIC ]
   { [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <compound-statement> (varname] 
      | AS [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <sql-statement> (varname] [/pandoc/div/div/horizontalrule/codeblock/span/span/varname
     {"varname"}) <sql-statement> (varname]... } (span]
```



<a name="loioabddfd62461747b08416521922da3577__section_gnn_mll_sqb"/>

## Parameters

 CREATE \[ OR REPLACE \]
 :   Parameter names must conform to the rules for database identifiers. They must have a valid SQL data type and be prefixed by the keyword IN, signifying that the argument is an expression that provides a value to the function.

    The CREATE clause creates a new function, while the OR REPLACE clause replaces an existing function with the same name. When a function is replaced, the definition of the function is changed but the existing permissions are preserved. You cannot use the OR REPLACE clause with temporary functions.

  TEMPORARY
 :   The function is visible only by the connection that created it, and that it is automatically dropped when the connection is dropped. Temporary functions can also be explicitly dropped. You cannot perform ALTER, GRANT, or REVOKE operations on them, and unlike other functions, temporary functions are not recorded in the catalog or transaction log.

    Temporary functions execute with the permissions of their creator \(current user\), and can only be owned by their creator. Therefore, do not specify owner when creating a temporary function. They can be created and dropped when connected to a read-only database.

  SQL SECURITY
 :   Defines whether the function is executed as the INVOKER, the user who is calling the function, or as the DEFINER, the user who owns the function. The default is DEFINER.

    When INVOKER is specified, more memory is used because annotation must be done for each user that calls the procedure. Also, name resolution is done as the invoker as well. Therefore, take care to qualify all object names \(tables, procedures, and so on\) with their appropriate owner.

  *<data-type\>*
 :   The data type of the parameter. Set the data type explicitly, or specify the %TYPE or %ROWTYPE attribute to set the data type to the data type of another object in the database. Use %TYPE to set it to the data type of a column in a table or view. Use %ROWTYPE to set the data type to a composite data type derived from a row in a table or view. LONG BINARY and LONG VARCHAR are not permitted as return-value data types.

  *<compound-statement\>*
 :   A set of SQL statements bracketed by BEGIN and END, and separated by semicolons. See *BEGIN … END Statement*.

  ON EXCEPTION RESUME
 :   Uses Transact-SQL-like error handling. See *CREATE PROCEDURE Statement*.

  \[NOT\] DETERMINISTIC
 :   Function is re-evaluated each time it is called in a query. The results of functions not specified in this manner may be cached for better performance, and re-used each time the function is called with the same parameters during query evaluation.

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
    FROM old_table
    ```

    Functions may be declared as DETERMINISTIC if they always return the same value for given input parameters. All user-defined functions are treated as deterministic unless they are declared NOT DETERMINISTIC. Deterministic functions return a consistent result for the same parameters and are free of side effects. That is, the database server assumes that two successive calls to the same function with the same parameters will return the same result without unwanted side-effects on the semantics of the query.

 

<a name="loioabddfd62461747b08416521922da3577__section_y2g_5gl_sqb"/>

## Remarks

To modify a user-defined function, or to hide the contents of a function by scrambling its definition, use the ALTER FUNCTION statement.

When functions are executed, not all parameters need to be specified. If a default value is provided in the CREATE FUNCTION statement, then missing parameters are assigned the default values. If an argument is not provided by the caller and no default is set, then an error is given.



### Required Parameters

For required parameters that accept variable names, an error is returned if one of the following conditions is true:

-   The variable does not exist
-   The contents of the variable are NULL
-   The variable exceeds the length allowed by the parameter
-   The data type of the variable does not match that required by the parameter



<a name="loioabddfd62461747b08416521922da3577__section_vjm_hwr_wwb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:

 Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:
 :   You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

  Connected directly to data lake Relational Engine as a data lake Relational Engine user:
 :   Function ownership determines the privilege required.

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



    For information on using a function created when connected as a data lake Relational Engine user, see [User-Defined Functions in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/abea6df6284d46c8b2265c477be1f704.html "User-defined functions are a class of procedures that return a single value to the calling environment.") :arrow_upper_right:.

 

<a name="loioabddfd62461747b08416521922da3577__section_vsq_xgl_sqb"/>

## Side Effects

Automatic commit



<a name="loioabddfd62461747b08416521922da3577__section_k12_ygl_sqb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioabddfd62461747b08416521922da3577__section_c5z_zgl_sqb"/>

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
    END
    ```

-   This example illustrates the use of the `fullname` function.

    -   Return a full name from two supplied strings:

        ```
        SELECT fullname ('joe','smith')
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
        FROM Employees
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
    RETURN @Result
    ```

    The statement `SELECT DoubleIt( 5 )` returns a value of `10`.


**Related Information**  


[CREATE FUNCTION Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a61796cb84f2101594a2b0b5a6993b95.html "Creates a user-defined function in the database. A function can be created for another user by specifying an owner name. Subject to permissions, a user-defined function can be used in exactly the same way as other non-aggregate functions.") :arrow_upper_right:

