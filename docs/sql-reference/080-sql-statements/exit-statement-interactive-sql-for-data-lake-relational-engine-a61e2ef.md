<!-- loioa61e2ef284f210159988cf268a58fd69 -->

# EXIT Statement \[Interactive SQL\] for Data Lake Relational Engine

Leaves Interactive SQL.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
{ EXIT | QUIT | BYE } [ <number> | <connection-variable> ]
```



<a name="loioa61e2ef284f210159988cf268a58fd69__IQ_Usage"/>

## Remarks

Closes the Interactive SQL window, if you are running Interactive SQL as a windowed program, or terminates Interactive SQL altogether when run in command-prompt \(batch\) mode. In both cases, the database connection is also closed. Before closing the database connection, Interactive SQL automatically executes a COMMIT statement, if the COMMIT\_ON\_EXIT option is set to ON. If this option is set to OFF, Interactive SQL performs an implicit ROLLBACK. By default, the COMMIT\_ON\_EXIT option is set to ON.

The optional return code can be used in batch files to indicate success or failure of the commands in an Interactive SQL command file. The default return code is 0.



<a name="loioa61e2ef284f210159988cf268a58fd69__IQ_Permissions"/>

## Privileges

None



<a name="loioa61e2ef284f210159988cf268a58fd69__IQ_Side_Effects"/>

## Side Effects

-   Automatically performs a commit, if option `COMMIT_ON_EXIT` is set to ON \(the default\); otherwise this statement performs an implicit rollback.



<a name="loioa61e2ef284f210159988cf268a58fd69__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not applicable by SAP Adaptive Server Enterprise.



<a name="loioa61e2ef284f210159988cf268a58fd69__IQ_Examples"/>

## Examples

The following example sets the Interactive SQL return value to 1 if there are any rows in table T, or to 0 if T contains no rows:

```
CREATE VARIABLE rowCount INT;
CREATE VARIABLE retcode INT;
SELECT COUNT(*) INTO rowCount FROM T;
IF( rowCount > 0 ) THEN
    SET retcode = 1;
ELSE
    SET retcode = 0;
END IF;
EXIT retcode;
```

You cannot write the following the statement, because EXIT is an Interactive SQL statement \(not a SQL statement\), and you cannot include any Interactive SQL statement in other SQL block statements:

```
CREATE VARIABLE rowCount INT; 
SELECT COUNT(*) INTO rowCount FROM T; 
IF( rowCount > 0 ) THEN     
    EXIT 1;    //  <-- not allowed 
ELSE 
    EXIT 0;    //  <-- not allowed 
END IF;
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

