<!-- loioa61fb00f84f21015a3cfb4fb0db739ea -->

# INCLUDE Statement \[ESQL\] for Data Lake Relational Engine

Includes a file into a source program to be scanned by the SQL source language preprocessor.



Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61fb00f84f21015a3cfb4fb0db739ea__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
INCLUDE <filename>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61fb00f84f21015a3cfb4fb0db739ea__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<filename\>*

</b></dt>
<dd>

Identifier



</dd>
</dl>



<a name="loioa61fb00f84f21015a3cfb4fb0db739ea__IQ_Usage"/>

## Remarks

The `INCLUDE` statement is very much like the C preprocessor `#include` directive.

However, the SQL preprocessor reads the given file, inserting its contents into the output C file. Thus, if an include file contains information that the SQL preprocessor requires, it should be included with the Embedded SQL `INCLUDE` statement.

Two file names are specially recognized: SQLCA and SQLDA. Any C program using Embedded SQL must contain this statement before any Embedded SQL statements:

```
EXEC SQL INCLUDE SQLCA
```

This statement must appear at a position in the C program where static variable declarations are allowed. Many Embedded SQL statements require variables \(invisible to the programmer\) which are declared by the SQL preprocessor at the position of the SQLCA include statement. The SQLDA file must be included if any SQLDAs are used.



<a name="loioa61fb00f84f21015a3cfb4fb0db739ea__IQ_Permissions"/>

## Privileges

None



<a name="loioa61fb00f84f21015a3cfb4fb0db739ea__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server

