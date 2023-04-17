<!-- loioa6227d8984f210159ad580e8826fdac0 -->

# RAISERROR Statement \[T-SQL\] for Data Lake Relational Engine

Allows user-defined errors to be signaled, and sends a message on the client.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
RAISERROR <error-number> [ <format-string> ] [, <arg-list >]
```



<a name="loioa6227d8984f210159ad580e8826fdac0__IQ_Parameters"/>

## Parameters

 *<error-number\>*
 :   A 5-digit integer greater than 17000. The error number is stored in the global variable *<@@error\>*.

  *<format-string\>*
 :   If not supplied or is empty, the error number is used to locate an error message in the system tables. SAP Adaptive Server Enterprise obtains messages 17000-19999 from the `SYSMESSAGES` table. In data lake Relational Engine, this table is an empty view, so errors in this range should provide a format string. Messages for error numbers of 20000 or greater are obtained from the `SYS.SYSUSERMESSAGES` table.

    The *<format-string\>* can be up to 255 bytes long. This is the same as in SAP ASE.

    The format string can contain placeholders for the arguments in the optional argument list. These placeholders are of the form `%nn!`, where *<nn\>* is an integer between 1 and 20.

 

<a name="loioa6227d8984f210159ad580e8826fdac0__IQ_Usage"/>

## Remarks

There is no comma between the *<error-number\>* and the *<format-string\>* parameters. The first item following a comma is interpreted as the first item in the argument list.

The extended values supported by the SQL Server or SAP ASE `RAISERROR` statement are not supported in data lake Relational Engine.

Intermediate RAISERROR status and code information is lost after the procedure terminates. If at return time an error occurs along with the RAISERROR, then the error information is returned and the RAISERROR information is lost. The application can query intermediate RAISERROR statuses by examining the `@@error` global variable at different execution points.



<a name="loioa6227d8984f210159ad580e8826fdac0__IQ_Permissions"/>

## Privileges

None



<a name="loioa6227d8984f210159ad580e8826fdac0__IQ_Standards"/>

## Standards

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioa6227d8984f210159ad580e8826fdac0__IQ_Examples"/>

## Examples

The following example raises error 99999, which is in the range for user-defined errors, and send a message to the client:

```
RAISERROR 99999 'Invalid entry for this 
column: %1!', @val
```

**Related Information**  


[CONTINUE\_AFTER\_RAISERROR Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/continue-after-raiserror-option-tsql-for-data-lake-relational-engine-a62fea0.md "Controls behavior following a RAISERROR statement.")

[ON\_TSQL\_ERROR Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/on-tsql-error-option-tsql-for-data-lake-relational-engine-a646abe.md "Controls error handling in stored procedures.")

