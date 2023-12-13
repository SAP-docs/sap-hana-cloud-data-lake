<!-- loioe7d81ab91c8d45718a7b786adc452f83 -->

# DROP MESSAGE Statement for Data Lake Relational Engine

Removes a message from the database.



<a name="loioe7d81ab91c8d45718a7b786adc452f83__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP MESSAGE <message-number>;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioe7d81ab91c8d45718a7b786adc452f83__IQ_Usage"/>

## Remarks

None



<a name="loioe7d81ab91c8d45718a7b786adc452f83__drop_datatype_privileges1"/>

## Privileges

-   Requires one of:
    -   You own the object
    -   DROP DATATYPE system privilege


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioe7d81ab91c8d45718a7b786adc452f83__IQ_Side_Effects"/>

## Side Effects

-   Automatic commit. Clears the Data window in dbisql.



<a name="loioe7d81ab91c8d45718a7b786adc452f83__IQ_Standards"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – supported by SAP Adaptive Server Enterprise



<a name="loioe7d81ab91c8d45718a7b786adc452f83__IQ_Examples"/>

## Examples

This example drops the message mymessage1 Num:

```
DROP MESSAGE mymessage1;
```

**Related Information**  


[CREATE MESSAGE Statement \[T-SQL\] for Data Lake Relational Engine](create-message-statement-t-sql-for-data-lake-relational-engine-a61829d.md "Adds a user-defined message to the SYSUSERMESSAGES system table for use by PRINT and RAISERROR statements.")

