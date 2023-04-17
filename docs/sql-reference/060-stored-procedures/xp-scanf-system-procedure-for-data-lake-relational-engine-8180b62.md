<!-- loio8180b6266ce210149e59fb0a2855a1a2 -->

# xp\_scanf System Procedure for Data Lake Relational Engine

Extracts substrings from an input string using a format string.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
xp_scanf(
<input_buffer>
, <format>
[ , <param1> [, <param2> ... ] ]
)
```



<a name="loio8180b6266ce210149e59fb0a2855a1a2__section_x2d_bct_tnb"/>

## Parameters

  *<input\_buffer\>* 
 :   Use this CHAR\(254\) parameter to specify the input string.

   *<format\>* 
 :   Use this CHAR\(254\) parameter to specify the format of the input string, using place holders \(%s\) for each *<param\>* argument. There can be up to fifty place holders in the *<format\>* argument, and there must be the same number of place holders as *<param\>* arguments.

   *<param1, param2, ...\>* 
 :   Use one or more of these CHAR\(254\) parameters to store the substrings extracted from *<input\_buffer\>*. There can be up to 50 of these parameters.

 

<a name="loio8180b6266ce210149e59fb0a2855a1a2__section_y2d_bct_tnb"/>

## Privileges

You need to have the EXECUTE privilege on the system procedure.



<a name="loio8180b6266ce210149e59fb0a2855a1a2__section_z2d_bct_tnb"/>

## Remarks

The xp\_scanf system procedure extracts substrings from an input string using the specified format, and puts the results in the specified parameter values.

Only the %s string format is supported. Other format specifiers such as %d and %f are not supported and scanning the input string stops if they are encountered.

