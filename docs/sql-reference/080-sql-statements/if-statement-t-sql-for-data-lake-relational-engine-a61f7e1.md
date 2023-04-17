<!-- loioa61f7e1784f210158874f5eb5969d8d7 -->

# IF Statement \[T-SQL\] for Data Lake Relational Engine

Provides conditional execution of a Transact-SQL statement, as an alternative to the data lake Relational Engine `IF` statement.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
 IF <expression>
   ... <statement>
   ... [ ELSE [ IF <expression> <statement> ]... ] 
```



<a name="loioa61f7e1784f210158874f5eb5969d8d7__IQ_Usage"/>

## Remarks

The Transact-SQL `IF` conditional and the `ELSE`  conditional each control the performance of only a single SQL statement or compound statement \(between the keywords `BEGIN` and `END`\).

In contrast to the data lake Relational Engine `IF` statement, the Transact-SQL `IF` statement has no `THEN`. The Transact-SQL version also has no `ELSEIF` or `END IF` keywords.

When comparing variables to the single value returned by a `SELECT` statement inside an `IF` statement, you must first assign the result of the `SELECT` to another variable.

> ### Note:  
> You cannot nest the `IF` statement.



<a name="loioa61f7e1784f210158874f5eb5969d8d7__IQ_Permissions"/>

## Privileges

None



<a name="loioa61f7e1784f210158874f5eb5969d8d7__IQ_Standards"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa61f7e1784f210158874f5eb5969d8d7__IQ_Examples"/>

## Examples

-   The following example uses the Transact-SQL `IF` statement:

    ```
    IF (SELECT max(id) FROM sysobjects) < 100
      RETURN
    ELSE
      BEGIN
        PRINT 'These are the user-created objects'
        SELECT name, type, id
        FROM sysobjects
        WHERE id < 100
    END
    ```

-   The following example uses of the Transact-SQL `ELSEIF` statement:

    ```
    
    BEGIN
     DECLARE @X INT
     SET @X = 1
     IF @X = 1
      PRINT '1'
      ELSEIF @X = 2
       PRINT '2'
      ELSE
       PRINT 'something else'
    END
    ```


