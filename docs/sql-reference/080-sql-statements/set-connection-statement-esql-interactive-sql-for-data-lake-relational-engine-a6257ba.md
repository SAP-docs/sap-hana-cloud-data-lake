<!-- loioa6257ba384f2101591acda39e1122d9f -->

# SET CONNECTION Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine

Changes the active database connection.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
SET CONNECTION [<connection-name>]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6257ba384f2101591acda39e1122d9f__IQ_Usage"/>

## Remarks

The current connection state is saved, and resumed when it again becomes the active connection. If you omit *<connection-name\>*, but a connection exists that was not named, that connection becomes the active connection.

> ### Note:  
> When cursors are opened in Embedded SQL, they are associated with the current connection. When the connection is changed, you cannot access the cursor names. The cursors remain active and in position and can become accessed when the associated connection becomes active again.



<a name="loioa6257ba384f2101591acda39e1122d9f__IQ_Permissions"/>

## Privileges

None



<a name="loioa6257ba384f2101591acda39e1122d9f__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar. Embedded SQL is a full-level feature.
-   SAP database products – supported by Open Client/Open Server.



<a name="loioa6257ba384f2101591acda39e1122d9f__IQ_Examples"/>

## Examples

The following example sets the current connection to the connection named "conn1" from `dbisql`:

```
SET CONNECTION conn1
```

**Related Information**  


[CONNECT Statement \[ESQL\] \[Interactive SQL\] for Data Lake Relational Engine](connect-statement-esql-interactive-sql-for-data-lake-relational-engine-a6164a2.md "Establishes a connection to the database identified by database-name running on the server identified by engine-name.")

[DISCONNECT Statement \[Interactive SQL\] for Data Lake Relational Engine](disconnect-statement-interactive-sql-for-data-lake-relational-engine-a61bf2a.md "Drops a connection with the database.")

