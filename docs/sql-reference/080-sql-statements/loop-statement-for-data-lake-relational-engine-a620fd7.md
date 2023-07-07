<!-- loioa620fd7984f21015bdfd809718fc3776 -->

# LOOP Statement for Data Lake Relational Engine

Repeats the execution of a statement list.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
[ <statement-label>: ]
... [ WHILE <search-condition> ] LOOP
... <statement-list>
... END LOOP [ <statement-label> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa620fd7984f21015bdfd809718fc3776__IQ_Usage"/>

## Remarks

The `WHILE` and `LOOP` statements are control statements that let you repeatedly execute a list of SQL statements while a *<search-condition\>* evaluates to TRUE. The `LEAVE` statement can be used to resume execution at the first statement after the `END LOOP`.

If the ending *<statement-label\>* is specified, it must match the beginning *<statement-label\>*.



<a name="loioa620fd7984f21015bdfd809718fc3776__IQ_Permissions"/>

## Privileges

None



<a name="loioa620fd7984f21015bdfd809718fc3776__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise. The `WHILE` statement provides looping in Transact-SQL stored procedures.



<a name="loioa620fd7984f21015bdfd809718fc3776__IQ_Examples"/>

## Examples

-   The following example shows a `WHILE` loop in a procedure:

    ```
    ...
    SET i = 1 ;
    WHILE i <= 10 LOOP
      INSERT INTO Counters( number ) VALUES ( i ) ;
      SET i = i + 1 ;
    END LOOP ;
    ...
    ```

-   The following example shows a labeled loop in a procedure:

    ```
    SET i = 1;
    lbl:
    LOOP
      INSERT
      INTO Counters( number )
      VALUES ( i ) ;
      IF i >= 10 THEN
        LEAVE lbl ;
      END IF ;
      SET i = i + 1 ;
    END LOOP lbl
    ```


**Related Information**  


[FOR Statement for Data Lake Relational Engine](for-statement-for-data-lake-relational-engine-a61e906.md "Repeats the execution of a statement list once for each row in a cursor.")

[LEAVE Statement for Data Lake Relational Engine](leave-statement-for-data-lake-relational-engine-a6206e0.md "Continues execution by leaving a compound statement or LOOP.")

[WHILE Statement \[T-SQL\] for Data Lake Relational Engine](while-statement-t-sql-for-data-lake-relational-engine-a62903f.md "Provides repeated execution of a statement or compound statement.")

