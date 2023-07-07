<!-- loio04d3a41e1d0c48aaaa788980a565bbe0 -->

# CALL Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Invokes a procedure.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).





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



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio04d3a41e1d0c48aaaa788980a565bbe0__section_e5m_gng_1rb"/>

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



<a name="loio04d3a41e1d0c48aaaa788980a565bbe0__section_p2g_hng_1rb"/>

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



<a name="loio04d3a41e1d0c48aaaa788980a565bbe0__section_ktc_2nr_wwb"/>

## Privileges



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio04d3a41e1d0c48aaaa788980a565bbe0__section_qmn_3ng_1rb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – not supported by SAP Adaptive Server Enterprise. For an alternative that is supported, see *EXECUTE Statement \[ESQL\]*.



<a name="loio04d3a41e1d0c48aaaa788980a565bbe0__section_wqb_jng_1rb"/>

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


[CALL Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a614c16084f21015bc34dd15aeb50bde.html "Invokes a procedure.") :arrow_upper_right:

