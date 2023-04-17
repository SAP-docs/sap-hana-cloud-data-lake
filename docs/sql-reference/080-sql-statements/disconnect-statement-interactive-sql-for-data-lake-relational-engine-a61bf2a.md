<!-- loioa61bf2a484f2101586c89bad47992194 -->

# DISCONNECT Statement \[Interactive SQL\] for Data Lake Relational Engine

Drops a connection with the database.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DISCONNECT [ { <connection-name> | CURRENT | ALL } ]
```



<a name="loioa61bf2a484f2101586c89bad47992194__IQ_Parameters"/>

## Parameters

 ALL
 :   Drops all of the connections of the application to all database environments.

  CURRENT
 :   \(Default\) drops the current connection.

 

<a name="loioa61bf2a484f2101586c89bad47992194__IQ_Usage"/>

## Remarks

The `DISCONNECT` statement drops a connection with the database server and releases all resources used by it. If the connection to be dropped was named on the `CONNECT` statement, the name can be specified.

An implicit `ROLLBACK` is executed on connections that are dropped.



<a name="loioa61bf2a484f2101586c89bad47992194__IQ_Permissions"/>

## Privileges

None



<a name="loioa61bf2a484f2101586c89bad47992194__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by Open Client/Open Server



<a name="loioa61bf2a484f2101586c89bad47992194__IQ_Examples"/>

## Examples

-   The following example uses `DISCONNECT` in Embedded SQL:

    ```
    EXEC SQL DISCONNECT :conn_name
    ```

-   The following example uses `DISCONNECT` from `dbisql` to disconnect all connections:

    ```
    DISCONNECT ALL
    ```


**Related Information**  


[CONNECT Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](connect-statement-esql-interactive-sql-for-data-lake-relational-engine-a6164a2.md "Establishes a connection to the database identified by database-name running on the server identified by engine-name.")

[SET CONNECTION Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](set-connection-statement-esql-interactive-sql-for-data-lake-relational-engine-a6257ba.md "Changes the active database connection.")

