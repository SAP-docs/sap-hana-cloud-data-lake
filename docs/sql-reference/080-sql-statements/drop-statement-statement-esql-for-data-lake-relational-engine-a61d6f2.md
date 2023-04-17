<!-- loioa61d6f2f84f2101587fbc546b2c34e86 -->

# DROP STATEMENT Statement \[ESQL\] for Data Lake Relational Engine

Frees resources used by the named prepared statement. These resources are allocated by a successful `PREPARE` statement, and are normally not freed until the database connection is released.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP STATEMENT [ <owner>.]<statement-name>
```



<a name="loioa61d6f2f84f2101587fbc546b2c34e86__IQ_Parameters"/>

## Parameters

 *<statement-name\>*
 :   Identifier or host-variable

 

<a name="loioa61d6f2f84f2101587fbc546b2c34e86__section_vwy_5wb_ccb"/>

## Remarks

To drop the statement, you must first have prepared the statement.



<a name="loioa61d6f2f84f2101587fbc546b2c34e86__IQ_Permissions"/>

## Privileges

None



<a name="loioa61d6f2f84f2101587fbc546b2c34e86__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by Open Client/Open Server



<a name="loioa61d6f2f84f2101587fbc546b2c34e86__IQ_Examples"/>

## Examples

The following example drops the statements `s1` and `stmt`:

```
EXEC SQL DROP STATEMENT S1;
EXEC SQL DROP STATEMENT :stmt;
```

**Related Information**  


[PREPARE Statement \[ESQL\] for Data Lake Relational Engine](prepare-statement-esql-for-data-lake-relational-engine-a621eea.md "Prepares a statement to be executed later or used for a cursor.")

