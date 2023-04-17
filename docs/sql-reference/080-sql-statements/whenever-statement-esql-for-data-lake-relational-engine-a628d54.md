<!-- loioa628d54984f210158db8a906f33f2297 -->

# WHENEVER Statement \[ESQL\] for Data Lake Relational Engine

Specifies error handling in an Embedded SQL program.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
WHENEVER
   { SQLERROR | SQLWARNING | NOTFOUND }
   … { GOTO <label> | STOP | CONTINUE | <C code;> }
```



<a name="loioa628d54984f210158db8a906f33f2297__IQ_Usage"/>

## Remarks

`WHENEVER` can be put anywhere in an Embedded SQL C program, and does not generate any code. The preprocessor generates code following each successive SQL statement. The error action remains in effect for all Embedded SQL statements from the source line of the `WHENEVER` statement until the next `WHENEVER` statement with the same error condition, or the end of the source file.

The default action is `CONTINUE`.

`WHENEVER` is provided for convenience in simple programs. Most of the time, checking the `sqlcode` field of the SQLCA \(SQLCODE\) directly is the easiest way to check error conditions. In this case, `WHENEVER` is not used. The `WHENEVER` statement causes the preprocessor to generate an *<if \( SQLCODE \)\>* test after each statement.

> ### Note:  
> The error conditions are in effect based on positioning in the C language source file and not on when the statements are executed.



<a name="loioa628d54984f210158db8a906f33f2297__IQ_Permissions"/>

## Privileges

None



<a name="loioa628d54984f210158db8a906f33f2297__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – supported by Open Client/Open Server



<a name="loioa628d54984f210158db8a906f33f2297__IQ_Examples"/>

## Examples

-   The following example executes `done` when the NOTFOUND clause is met:

    ```
    EXEC SQL WHENEVER NOTFOUND GOTO done;
    ```

-   The following example uses the SQLERROR clause:

    ```
    EXEC SQL WHENEVER SQLERROR
    	{ 
    		PrintError( &sqlca ); 
    		return( FALSE ); 
    	};
    ```


