<!-- loio8180c9106ce21014894dc48bcbd02bb5 -->

# xp\_sprintf System Procedure for Data Lake Relational Engine

Builds a result string from a set of input strings.



<a name="loio8180c9106ce21014894dc48bcbd02bb5__section_i52_dcb_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
xp_sprintf(
<buffer>
, <format>
[ , <param1> [, <param2> ... ] ]
)
```



<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_parm1"/>

## Parameters


<dl>
<dt><b>

*<buffer\>* 

</b></dt>
<dd>

This is a CHAR\(254\) OUT parameter that is filled in with the formatted result.



</dd><dt><b>

*<format\>* 

</b></dt>
<dd>

Use this CHAR\(254\) parameter to specify how to format the result string, using place holders \(%s\) for each *<param\>* argument. There can be up to fifty place holders in the *<format\>* argument, and there should be the same number of place holders as *<param\>* arguments. Only the %s string format is supported.



</dd><dt><b>

*<param1, param2\>* 

</b></dt>
<dd>

The input strings that are used in the result string. You can specify up to 50 of these CHAR\(254\) arguments.



</dd>
</dl>



<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_results1"/>

## Result Set

None



<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_remarks1"/>

## Remarks

The result placed in the output parameter is truncated to 254 characters.



<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.



<a name="loio8180c9106ce21014894dc48bcbd02bb5__xp_sprintfs_examples1"/>

## Examples

```
--- Setup for the following examples ---
CREATE VARIABLE result CHAR( 254 );
```

This example puts the string Hello World! into the result variable.

```
CALL xp_sprintf( result, '%s %s', 'Hello', 'World!' );
SELECT result;
```

This example formats the year, month, and day into a date string.

```
CALL xp_sprintf( result, '%s/%s/%s', 2014, 11, 23 );
SELECT result;
```

**Related Information**  


[xp_sprintf System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/bcaf180e679e43d78733830fb7e4c2fa.html "Builds a result string from a set of input strings.") :arrow_upper_right:

