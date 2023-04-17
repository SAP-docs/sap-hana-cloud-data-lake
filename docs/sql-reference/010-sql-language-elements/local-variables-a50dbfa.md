<!-- loioa50dbfab84f21015b2e4da36a3467308 -->

# Local Variables

Local variables are declared by the user, and can be used in procedures or in batches of SQL statements to hold information.



Local variables are declared using the `DECLARE` statement, which can be used only within a compound statement \(that is, bracketed by the `BEGIN` and `END` keywords\). The variable is initially set as NULL. You can set the value of the variable using the `SET` statement, or you can assign the value using a `SELECT` statement with an `INTO` clause.

The syntax of the `DECLARE` statement is as follows:

```
DECLARE variable-name data-type
```

You can pass local variables as arguments to procedures, as long as the procedure is called from within the compound statement.



<a name="loioa50dbfab84f21015b2e4da36a3467308__iq_refbb_136"/>

## Examples

-   The following batch illustrates the use of local variables:

    ```
    BEGIN
    	DECLARE local_var INT ;
    	SET local_var = 10 ;
    	MESSAGE 'local_var = ', local_var ;
    END
    ```

    Running this batch from ISQL displays this message on the server window:

    ```
    local_var = 10
    ```

-   The variable `local_var` does not exist outside the compound statement in which it is declared. The following batch is invalid, and displays a "column not found" error:

    ```
    -- This batch is invalid.
    BEGIN
    	DECLARE local_var INT ;
    	SET local_var = 10 ;
    	MESSAGE 'local_var = ', local_var ;
    END;
    MESSAGE 'local_var = ', local_var ;
    ```

-   The following example illustrates the use of `SELECT` with an `INTO` clause to set the value of a local variable:

    ```
    BEGIN
    	DECLARE local_var INT ;
    	SELECT 10 INTO local_var ;
    	MESSAGE 'local_var = ', local_var ;
    END
    ```

    Running this batch from ISQL displays this message on the server window:

    ```
    local_var = 10
    ```




<a name="loioa50dbfab84f21015b2e4da36a3467308__iq_refbb_137"/>

## Compatibility

-   Names – Both SAP Adaptive Server Enterprise and data lake Relational Engine support local variables. In SAP ASE, the all variables require an @ sign as their prefix. In data lake Relational Engine, the @ prefix is optional. To write compatible SQL, ensure all your variables have the @ prefix.
-   Scope – The scope of local variables differs between data lake Relational Engine and SAP ASE. Data lake Relational Engine supports the use of the `DECLARE` statement to declare local variables within a batch. However, if the `DECLARE` is executed within a compound statement, the scope is limited to the compound statement.
-   Declaration – Only one variable can be declared for each `DECLARE` statement in data lake Relational Engine. In SAP ASE, more than one variable can be declared in a single statement.

