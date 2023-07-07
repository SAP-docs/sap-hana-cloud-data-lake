<!-- loioa554461384f21015aca0af2a35f9c2a7 -->

# GROUPING Function \[Aggregate\] for Data Lake Relational Engine

Identifies whether a column in a `ROLLUP` or `CUBE` operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.



```
GROUPING ( <group-by-expression> ) 
```



<a name="loioa554461384f21015aca0af2a35f9c2a7__GROUPING_parm1"/>

## Parameters


<dl>
<dt><b>

*<group-by-expression\>*

</b></dt>
<dd>

An expression appearing as a grouping column in the result set of a query that uses a GROUP BY clause with the ROLLUP or CUBE keyword. The function identifies subtotal rows added to the result set by a ROLLUP or CUBE operation.



</dd>
</dl>



<a name="loioa554461384f21015aca0af2a35f9c2a7__GROUPING_returns1"/>

## Returns

-   1 – indicates that *<group-by-expression\>* is NULL because it is part of a subtotal row. The column is not a prefix column for that row.
-   0 – indicates that *<group-by-expression\>* is a prefix column of a subtotal row.



<a name="loioa554461384f21015aca0af2a35f9c2a7__GROUPING_remarks1"/>

## Remarks

Data lake Relational Engine does not support the PERCENTILE\_CONT or PERCENTILE\_DISC functions with GROUP BY CUBE operations.



<a name="loioa554461384f21015aca0af2a35f9c2a7__GROUPING_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[GROUPING Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/259511aa310241949d6e8389561dc62c.html "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.") :arrow_upper_right:

