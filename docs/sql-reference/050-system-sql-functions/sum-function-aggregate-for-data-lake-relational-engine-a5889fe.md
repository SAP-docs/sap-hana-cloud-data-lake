<!-- loioa5889fe484f21015b024abf6dcede473 -->

# SUM Function \[Aggregate\] for Data Lake Relational Engine

Returns the total of the specified expression for each group of rows.



```
SUM ( <expression> | DISTINCT <column-name> );
```



<a name="loioa5889fe484f21015b024abf6dcede473__SUM_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The object to be summed. This is commonly a column name.



</dd><dt><b>

DISTINCT *<column-name\>*

</b></dt>
<dd>

Computes the sum of the unique values in *<column-name\>* for each group of rows. This is of limited usefulness, but is included for completeness.



</dd>
</dl>



<a name="loioa5889fe484f21015b024abf6dcede473__SUM_returns1"/>

## Result Set

-   INTEGER
-   DOUBLE
-   NUMERIC
-   BIGINT \(SIGNED or UNSIGNED\)



<a name="loioa5889fe484f21015b024abf6dcede473__SUM_remarks1"/>

## Remarks

Rows where the specified expression is NULL are not included.

Returns NULL for a group containing no rows.



<a name="loioa5889fe484f21015b024abf6dcede473__SUM_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa5889fe484f21015b024abf6dcede473__SUM_example1"/>

## Examples

The following statement returns the value 3749146.740:

```
SELECT SUM( salary )
FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[AVG Function \[Aggregate\] for Data Lake Relational Engine](avg-function-aggregate-for-data-lake-relational-engine-a535f04.md "Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.")

[COUNT Function \[Aggregate\] for Data Lake Relational Engine](count-function-aggregate-for-data-lake-relational-engine-a54290f.md "Counts the number of rows in a group, depending on the specified parameters.")

[SUM Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/d656f224db9a4567a7ba604993702e94.html "Returns the total of the specified expression for each group of rows.") :arrow_upper_right:

