<!-- loio8180c9106ce21014894dc48bcbd02bb5 -->

# xp\_sprintf System Procedure for Data Lake Relational Engine

Builds a result string from a set of input strings.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
xp_sprintf(
<buffer>
, <format>
[ , <param1> [, <param2> ... ] ]
)
```



<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_parm1"/>

## Parameters

  *<buffer\>* 
 :   This is a CHAR\(254\) OUT parameter that is filled in with the formatted result.

   *<format\>* 
 :   Use this CHAR\(254\) parameter to specify how to format the result string, using place holders \(%s\) for each *<param\>* argument. There can be up to fifty place holders in the *<format\>* argument, and there should be the same number of place holders as *<param\>* arguments. Only the %s string format is supported.

   *<param1, param2\>* 
 :   The input strings that are used in the result string. You can specify up to 50 of these CHAR\(254\) arguments.

 

<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_remarks1"/>

## Remarks

The result placed in the output parameter is truncated to 254 characters.



<a name="loio8180c9106ce21014894dc48bcbd02bb5__section_fdb_b3j_snb"/>

## Privileges

You need to have the EXECUTE privilege on the system procedure.



The following statements put the string Hello World! into the result variable.

```
CREATE VARIABLE result CHAR( 254 );
CALL dbo.xp_sprintf( result, '%s %s', 'Hello', 'World!' );
SELECT result;
```

The following statements format the year, month, and day into a date string.

```
CREATE VARIABLE result CHAR( 254 );
CALL dbo.xp_sprintf( result, '%s/%s/%s', 2014, 11, 23 );
SELECT result;
```

**Related Information**  


[xp_sprintf System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/bcaf180e679e43d78733830fb7e4c2fa.html "Builds a result string from a set of input strings.") :arrow_upper_right:

