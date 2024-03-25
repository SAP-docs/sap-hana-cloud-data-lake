<!-- loiof82be4309ee34e0dab5a3148c3d56fc6 -->

# ISNUMERIC Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Tests whether a string argument can be converted to a numeric.



```
ISNUMERIC ( <string> );
```



<a name="loiof82be4309ee34e0dab5a3148c3d56fc6__section_fdy_2kh_trb"/>

## Parameters


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

The string to be analyzed to determine whether the string represents a valid numeric value.



</dd>
</dl>



<a name="loiof82be4309ee34e0dab5a3148c3d56fc6__section_i3p_fkh_trb"/>

## Result Set

INT



<a name="loiof82be4309ee34e0dab5a3148c3d56fc6__section_vzd_gkh_trb"/>

## Remarks

If a conversion is possible, the function returns 1; otherwise, it returns 0. If the argument is null, 0 is returned.



<a name="loiof82be4309ee34e0dab5a3148c3d56fc6__section_iwm_1mh_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loiof82be4309ee34e0dab5a3148c3d56fc6__section_tys_bmh_trb"/>

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
from MyData;
```

**Related Information**  


[ISNUMERIC Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a55af5d284f21015867a9c978b63f5c1.html "Tests whether a string argument can be converted to a numeric.") :arrow_upper_right:

