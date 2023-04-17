<!-- loioa61af09b84f210159eb9f4cf073f053d -->

# DECLARE CURSOR Statement \[T-SQL\] for Data Lake Relational Engine

Declares a cursor that is compatible with SAP Adaptive Server Enterprise.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DECLARE <cursor-name>
   … CURSOR FOR <select-statement>
   …[ FOR { READ ONLY | UPDATE } ]
```



<a name="loioa61af09b84f210159eb9f4cf073f053d__IQ_Usage"/>

## Remarks

Data lake Relational Engine supports a `DECLARE CURSOR` syntax that is not supported in SAP ASE. For information on the full `DECLARE CURSOR` syntax, see *DECLARE CURSOR Statement \[ESQL\] \[SP\]*.

> ### Note:  
> Use the `sp_iqcursorinfo` system procedure to display detailed information about cursors currently open on the server.



<a name="loioa61af09b84f210159eb9f4cf073f053d__IQ_Permissions"/>

## Privilege

None



<a name="loioa61af09b84f210159eb9f4cf073f053d__IQ_Standards"/>

## Standards

-   SQL – the `FOR UPDATE` and `FOR READ ONLY` options are Transact-SQL extensions to ISO/ANSI SQL grammar.
-   SAP database products – there are some features of the SAP ASE `DECLARE CURSOR` statement that are not supported in data lake Relational Engine.
    -   In the data lake Relational Engine dialect, `DECLARE CURSOR` in a procedure or batch must immediately follow the BEGIN keyword. In the Transact-SQL dialect, there is no such restriction.
    -   In SAP ASE, when a cursor is declared in a procedure or batch, it exists for the duration of the procedure or batch. In data lake Relational Engine, if a cursor is declared inside a compound statement, it exists only for the duration of that compound statement \(whether it is declared in a data lake Relational Engine or Transact-SQL compound statement\).


**Related Information**  


[DECLARE CURSOR Statement \[ESQL\] \[SP\] for Data Lake Relational Engine](declare-cursor-statement-esql-sp-for-data-lake-relational-engine-a61ac0b.md "Declares a cursor. Cursors are the primary means for manipulating the results of queries.")

[sp\_iqcursorinfo Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqcursorinfo-procedure-for-data-lake-relational-engine-a5a1c74.md "Displays detailed information about cursors currently open on the server.")

