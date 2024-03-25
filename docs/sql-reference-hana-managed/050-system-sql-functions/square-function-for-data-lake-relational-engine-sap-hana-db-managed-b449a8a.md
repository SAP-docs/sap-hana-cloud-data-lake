<!-- loiob449a8a0b1e949ef81aceed2ee770dd3 -->

# SQUARE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the square of the specified expression as a float.



```
SQUARE ( <numeric-expression> );
```



<a name="loiob449a8a0b1e949ef81aceed2ee770dd3__section_gh3_2w5_vrb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

Is a column, variable, or expression with a data type that is either exact numeric, approximate numeric, money, or any type that can be implicitly converted to one of these types. For other data types, the SQUARE function generates an error. The return value is of DOUBLE data type.



</dd>
</dl>



<a name="loiob449a8a0b1e949ef81aceed2ee770dd3__section_nwv_2w5_vrb"/>

## Remarks

`SQUARE` function takes one argument. For example, `SQUARE` \(*<12.01\>*\) returns 144.240100.



<a name="loiob449a8a0b1e949ef81aceed2ee770dd3__section_kgj_fw5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise

**Related Information**  


[SQUARE Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a582f08784f210158c9aebe92c8ae80f.html "Returns the square of the specified expression as a float.") :arrow_upper_right:

