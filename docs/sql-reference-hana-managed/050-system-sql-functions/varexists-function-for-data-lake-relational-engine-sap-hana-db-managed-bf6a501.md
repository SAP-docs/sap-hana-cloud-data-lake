<!-- loiobf6a50154e834de2b212bb738f57143a -->

# VAREXISTS Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns 1 if a user-defined variable exists with the specified name. Returns 0 if no such variable exists.



```
VAREXISTS( <variable-name-string> [, <owner> ] )
```



<a name="loiobf6a50154e834de2b212bb738f57143a__section_wrt_dfv_vrb"/>

## Parameters


<dl>
<dt><b>

*<variable-name-string\>* 

</b></dt>
<dd>

The name of the variable to be tested, as a string \(for example, 'myVariable'\).



</dd><dt><b>

*<owner\>*

</b></dt>
<dd>

The user ID of the owner of the variable, as a string. *<owner\>* is only for use with owned database-scope variables.



</dd>
</dl>



<a name="loiobf6a50154e834de2b212bb738f57143a__section_dxl_2fv_vrb"/>

## Returns

INT



<a name="loiobf6a50154e834de2b212bb738f57143a__section_dpc_ffv_vrb"/>

## Standards and Compatibility


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



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


[VAREXISTS Function [Miscellaneous] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/81ffd1036ce210149ae9c943fab6d1c1.html "Returns 1 if a user-defined variable exists with the specified name. Returns 0 if no such variable exists.") :arrow_upper_right:

