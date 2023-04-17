<!-- loioa625ac1c84f210158638b81051dcd9b9 -->

# SET DESCRIPTOR Statement \[ESQL\] for Data Lake Relational Engine

Describes the variables in a SQL descriptor area, and places data into the descriptor area.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET DESCRIPTOR <descriptor-name>
   … { COUNT = { <integer> | <hostvar> }
     | VALUE <n> <assignment> [, …] }
```

```
<assignment> ::=
   { { TYPE | SCALE | PRECISION | LENGTH | INDICATOR } = { <integer> | <hostvar> } 
   | DATA = <hostvar> }
```



<a name="loioa625ac1c84f210158638b81051dcd9b9__IQ_Parameters"/>

## Parameters

 COUNT
 :   Sets the number of described variables within the descriptor area.

  VALUE
 :   The value *<n\>* specifies the variable in the descriptor area upon which the assignments are performed.

  DATA
 :   Type checking is performed when using the DATA clause to ensure that the variable in the descriptor area has the same type as the host variable. If an error occurs, the code is returned in the SQLCA.

 

<a name="loioa625ac1c84f210158638b81051dcd9b9__IQ_Permissions"/>

## Privileges

None



<a name="loioa625ac1c84f210158638b81051dcd9b9__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server

