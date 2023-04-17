<!-- loioa6221e2a84f210159efdf11b85fd25e8 -->

# PRINT Statement \[T-SQL\] for Data Lake Relational Engine

Displays a message on the message window of the database server.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
PRINT <format-string> [, <arg-list>]
```



<a name="loioa6221e2a84f210159efdf11b85fd25e8__IQ_Usage"/>

## Remarks

The `PRINT` statement returns a message to the client window if you are connected from an Open Client application or JDBC application. If you are connected from an Embedded SQL or ODBC application, the message displays on the database server window.

The format string can contain placeholders for the arguments in the optional argument list. These placeholders are of the form *<%nn!\>*, where *<nn\>* is an integer between 1 and 20.



<a name="loioa6221e2a84f210159efdf11b85fd25e8__IQ_Permissions"/>

## Privileges

None



<a name="loioa6221e2a84f210159efdf11b85fd25e8__IQ_Standards"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa6221e2a84f210159efdf11b85fd25e8__IQ_Examples"/>

## Examples

-   The following example displays a message on the server message window:

    ```
    CREATE PROCEDURE print_test
    AS
    PRINT 'Procedure called successfully'
    ```

-   This statement returns the string ***Procedure called successfully*** to the client:

    ```
    EXECUTE print_test
    ```

-   The following example uses placeholders in the `PRINT` statement; execute these statements inside a procedure:

    ```
    DECLARE @var1 INT, @var2 INT
    SELECT @var1 = 3, @var2 = 5
    PRINT 'Variable 1 = %1!, Variable 2 = %2!', @var1, @var2
    ```

-   The following example uses `RAISERROR` to disallow connections:

    ```
    CREATE procedure DBA.login_check() 
    begin
      // Allow a maximum of 3 concurrent connections
      IF( db_property('ConnCount') > 3 ) then
      raiserror 28000
        'User %1! is not allowed to connect -- there are
          already %2! users logged on',
          current user,  
          cast(db_property('ConnCount') as int)-1;
        ELSE 
      call sp_login_environment; 
        end if;
    end
    go
    grant execute on DBA.login_check to PUBLIC
    go
    set option PUBLIC.Login_procedure='DBA.login_check' 
    go
    ```

    For an alternate way to disallow connections, use the `LOGIN_PROCEDURE` option or the `sp_iqmodifylogin` system stored procedure.


**Related Information**  


[LOGIN\_PROCEDURE Option for Data Lake Relational Engine](../090-database-options/login-procedure-option-for-data-lake-relational-engine-a63d00e.md "Specifies a login procedure that sets connection compatibility options at start-up.")

