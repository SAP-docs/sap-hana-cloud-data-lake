<!-- loioa55af5d284f21015867a9c978b63f5c1 -->

# ISNUMERIC Function \[Miscellaneous\] for Data Lake Relational Engine

Tests whether a string argument can be converted to a numeric.



```
ISNUMERIC ( <string> )
```



<a name="loioa55af5d284f21015867a9c978b63f5c1__ISNUMERIC_parm1"/>

## Parameters

 *<string\>*
 :   The string to be analyzed to determine whether the string represents a valid numeric value.

 

<a name="loioa55af5d284f21015867a9c978b63f5c1__ISNUMERIC_returns1"/>

## Returns

INT



<a name="loioa55af5d284f21015867a9c978b63f5c1__ISNUMERIC_remarks1"/>

## Remarks

If a conversion is possible, the function returns 1; otherwise, it returns 0. If the argument is null, 0 is returned.



<a name="loioa55af5d284f21015867a9c978b63f5c1__ISNUMERIC_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55af5d284f21015867a9c978b63f5c1__ISNUMERIC_example1"/>

## Example

The following example tests whether the height\_in\_cms column holds valid numeric data, returning invalid numeric data as NULL, and valid numeric data in int format:

```
data height_in_cms
------------------------
asde
asde
180
156
```

```
select case
   when isnumeric(height_in_cms)=0
   then NULL
   else cast(height_in_cms as int) 
   end
from MyData
```

**Related Information**  


[ISNUMERIC Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/f82be4309ee34e0dab5a3148c3d56fc6.html "Tests whether a string argument can be converted to a numeric.") :arrow_upper_right:

