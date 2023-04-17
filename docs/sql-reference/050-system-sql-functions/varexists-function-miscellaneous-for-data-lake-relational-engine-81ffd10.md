<!-- loio81ffd1036ce210149ae9c943fab6d1c1 -->

# VAREXISTS Function \[Miscellaneous\] for Data Lake Relational Engine

Returns 1 if a user-defined variable exists with the specified name. Returns 0 if no such variable exists.



```
VAREXISTS( <variable-name-string> [, <owner> ] )
```



<a name="loio81ffd1036ce210149ae9c943fab6d1c1__VAREXISTS_parm1"/>

## Parameters

 *<variable-name-string\>* 
 :   The name of the variable to be tested, as a string \(for example, 'myVariable'\).

  *<owner\>*
 :   The user ID of the owner of the variable, as a string. *<owner\>* is only for use with owned database-scope variables.

 

<a name="loio81ffd1036ce210149ae9c943fab6d1c1__VAREXISTS_returns1"/>

## Returns

INT



<a name="loio81ffd1036ce210149ae9c943fab6d1c1__VAREXISTS_standards1"/>

## Standards and Compatibility

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

The following IF statement checks to see if a variable called start\_time exists. If it doesn't, then the database server creates a connection-scope variable with that name, and sets its value to the current time.

```
IF VAREXISTS( 'start_time' ) = 0 THEN
    CREATE VARIABLE start_time TIMESTAMP;
END IF;
SET start_time = CURRENT TIMESTAMP;
```

The following IF statement checks to see if a database-scope variable named run\_time owned by user ID jsmith exists. If it doesn't, then the database server creates the variable, and sets its value to the current time.

```
IF VAREXISTS( 'run_time', 'jsmith' ) = 0 THEN
    CREATE DATABASE VARIABLE jsmith.run_time TIMESTAMP = CURRENT TIMESTAMP;
END IF;
```

**Related Information**  


[VAREXISTS Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/bf6a50154e834de2b212bb738f57143a.html "Returns 1 if a user-defined variable exists with the specified name. Returns 0 if no such variable exists.") :arrow_upper_right:

