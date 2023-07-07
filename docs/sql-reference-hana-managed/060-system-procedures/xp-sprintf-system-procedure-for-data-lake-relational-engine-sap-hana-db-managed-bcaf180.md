<!-- loiobcaf180e679e43d78733830fb7e4c2fa -->

# xp\_sprintf System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Builds a result string from a set of input strings.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
xp_sprintf(
<buffer>
, <format>
[ , <param1> [, <param2> ... ] ]
)
```



<a name="loiobcaf180e679e43d78733830fb7e4c2fa__section_qwl_x42_srb"/>

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



<a name="loiobcaf180e679e43d78733830fb7e4c2fa__section_wxy_x42_srb"/>

## Remarks

The result placed in the output parameter is truncated to 254 characters.



## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



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


[xp_sprintf System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8180c9106ce21014894dc48bcbd02bb5.html "Builds a result string from a set of input strings.") :arrow_upper_right:

