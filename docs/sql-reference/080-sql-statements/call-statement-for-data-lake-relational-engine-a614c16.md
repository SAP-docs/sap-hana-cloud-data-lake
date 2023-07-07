<!-- loioa614c16084f21015bc34dd15aeb50bde -->

# CALL Statement for Data Lake Relational Engine

Invokes a procedure.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.





### Syntax 1

```
[ <variable> = ] CALL { <owner> | <schema-name> }<procedure-name> ( [ <expression> ] [ , … ] ) 
    [ AS USER { <string> | <variable> } IDENTIFIED BY { <string> | <variable> } ]
```



### Syntax 2

```
[ <variable> = ] CALL { <owner> | <schema-name> }<procedure-name> ( [ <parameter-name> = <expression> ] [ , … ] ) 
    [ AS USER { <string> | <variable> } IDENTIFIED BY { <string> | <variable> } ]
```



<a name="loioa614c16084f21015bc34dd15aeb50bde__call_parameters1"/>

## Parameters


<dl>
<dt><b>

AS USER ... IDENTIFIED BY clause

</b></dt>
<dd>

\(Optional\) Calls a procedure or function as a different user. The database server verifies that the user ID and password provided are valid, and then executes the procedure or function as the specified user. The invoker of the procedure is the specified user. Upon exiting the procedure or function, the user context is restored to its original state.

> ### Note:  
> All string values must be enclosed in single quotes; otherwise the database server interprets them as variable names.



</dd>
</dl>



<a name="loioa614c16084f21015bc34dd15aeb50bde__call_remarks1"/>

## Remarks

CALL invokes a procedure that has been previously created with a CREATE PROCEDURE statement. When the procedure completes, any INOUT or OUT parameter values are copied back.

> ### Note:  
> The AS USER ... IDENTIFIED BY clause only applies to the CALL statement and is not supported for procedures in the FROM clause or functions in the select list.

You can specify the argument list by position or by using keyword format. By position, arguments match up with the corresponding parameter in the parameter list for the procedure. By keyword, arguments match the named parameters.

Procedure arguments can be assigned default values in the CREATE PROCEDURE statement, and missing parameters are assigned the default value, or, if no default is set, NULL.

Inside a procedure, CALL can be used in a DECLARE statement when the procedure returns result sets.

> ### Note:  
> You cannot reference a Table UDF in a CALL SQL statement.

Procedures can return an integer value \(as a status indicator, say\) using the RETURN statement. You can save this return value in a variable using the equality sign as an assignment operator:

```
CREATE VARIABLE returnval INT ;
returnval = CALL proc_integer ( arg1 = val1, ... )
```

> ### Note:  
> Use of this statement to invoke a function is deprecated. To call functions, use an assignment statement to invoke the function and assign its result to a variable. For example:
> 
> ```
> DECLARE varname INT;
> SET varname=test( );
> ```



<a name="loioa614c16084f21015bc34dd15aeb50bde__call_privileges1"/>

## Privileges



### 

Requires one of:

-   You own the procedure.
-   EXECUTE ANY PROCEDURE system privilege.
-   EXECUTE object-level privilege for the procedure.
-   EXECUTE PROCEDURE object-level privilege on the schema containing the procedure if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa614c16084f21015bc34dd15aeb50bde__call_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. For an alternative that is supported, see *EXECUTE Statement \[ESQL\]*.



<a name="loioa614c16084f21015bc34dd15aeb50bde__call_examples1"/>

## Examples

-   The following example calls the sp\_customer\_list procedure. This procedure has no parameters, and returns a result set:

    ```
    CALL sp_customer_list()
    ```

-   The following example creates a procedure to return the number of orders placed by the customer whose ID is supplied, creates a variable to hold the result, calls the procedure, and displays the result:

    ```
    CREATE PROCEDURE OrderCount (IN CustomerID INT, OUT Orders INT)
    BEGIN
    SELECT COUNT("DBA".SalesOrders.ID)
    INTO Orders
    FROM "DBA".Customers
    KEY LEFT OUTER JOIN "DBA".SalesOrders
    WHERE "DBA".Customers.ID = CustomerID ;
    END
    go
    -- Create a variable to hold the result
    CREATE VARIABLE Orders INT
    go
    
    -- Call the procedure, FOR customer 101
    -- -----------------------------
    CALL OrderCount ( 101, Orders) 
    go
    --------------------------------
    --  Display the result
    SELECT Orders FROM DUMMY 
    go
    ```


**Related Information**  


[CALL Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/04d3a41e1d0c48aaaa788980a565bbe0.html "Invokes a procedure.") :arrow_upper_right:

[CREATE PROCEDURE Statement for Data Lake Relational Engine](create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

[EXECUTE Statement \[ESQL\] for Data Lake Relational Engine](execute-statement-esql-for-data-lake-relational-engine-a774406.md "Executes a SQL statement.")

