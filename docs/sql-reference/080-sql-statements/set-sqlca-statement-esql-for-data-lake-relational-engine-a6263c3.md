<!-- loioa6263c3584f21015b49c8e4956f4ca03 -->

# SET SQLCA Statement \[ESQL\] for Data Lake Relational Engine

Tells the SQL preprocessor to use a SQLCA other than the default global *<sqlca\>*.



<a name="loioa6263c3584f21015b49c8e4956f4ca03__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET SQLCA <sqlca>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6263c3584f21015b49c8e4956f4ca03__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<sqlca\>*

</b></dt>
<dd>

Identifier or string



</dd>
</dl>



<a name="loioa6263c3584f21015b49c8e4956f4ca03__IQ_Usage"/>

## Remarks

The current SQLCA pointer is implicitly passed to the database interface library on every Embedded SQL statement. All Embedded SQL statements that follow this statement in the C source file use the new SQLCA. This statement is necessary only when you are writing code that is reentrant. The *<sqlca\>* should reference a local variable. Any global or module static variable is subject to being modified by another thread.



<a name="loioa6263c3584f21015b49c8e4956f4ca03__IQ_Permissions"/>

## Privileges

None



<a name="loioa6263c3584f21015b49c8e4956f4ca03__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by Open Client/Open Server

