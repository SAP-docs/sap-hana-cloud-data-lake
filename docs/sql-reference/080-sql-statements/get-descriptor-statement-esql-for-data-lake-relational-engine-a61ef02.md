<!-- loioa61ef02b84f21015b3c49fa3b77706f3 -->

# GET DESCRIPTOR Statement \[ESQL\] for Data Lake Relational Engine

Retrieves information about variables within a descriptor area, or retrieves actual data from a variable in a descriptor area.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GET DESCRIPTOR <descriptor-name>
    { <...hostvar> = COUNT } | VALUE <n> <assignment> [,…] }
```

```
<assignment> ::=
   <hostvar> = { TYPE 
   | LENGTH 
   | PRECISION 
   | SCALE 
   | DATA 
   | INDICATOR 
   | NAME 
   | NULLABLE 
   | RETURNED_LENGTH }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61ef02b84f21015b3c49fa3b77706f3__IQ_Usage"/>

## Remarks

The value *<n\>* specifies the variable in the descriptor area about which information is retrieved.

Type checking is performed when doing `GET DESCRIPTOR ... DATA` to ensure that the host variable and the descriptor variable have the same data type. `LONG VARCHAR` and `LONG BINARY` are not supported by `GET DESCRIPTOR ... DATA`.

If an error occurs, it is returned in the SQLCA.



<a name="loioa61ef02b84f21015b3c49fa3b77706f3__IQ_Permissions"/>

## Privileges

None



<a name="loioa61ef02b84f21015b3c49fa3b77706f3__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server

**Related Information**  


[SET DESCRIPTOR Statement \[ESQL\] for Data Lake Relational Engine](set-descriptor-statement-esql-for-data-lake-relational-engine-a625ac1.md "Describes the variables in a SQL descriptor area, and places data into the descriptor area.")

