<!-- loioa54290fd84f21015b7dddc9484de19d0 -->

# COUNT Function \[Aggregate\] for Data Lake Relational Engine

Counts the number of rows in a group, depending on the specified parameters.



```
COUNT ( * | <expression> | DISTINCT <column-name> )
```



<a name="loioa54290fd84f21015b7dddc9484de19d0__COUNT_parm1"/>

## Parameters

 \*
 :   Returns the number of rows in each group.

    > ### Note:  
    > When the query results are displayed, the \* is not displayed in the column header, and appears as:
    > 
    > ```
    > Count()
    > ```

  *<expression\>*
 :   Returns the number of rows in each group where expression is not the NULL value.

  DISTINCT *<column-name\>*
 :   Returns the number of different values in column-name. Rows where the value is the NULL value are not included in the count.

 

<a name="loioa54290fd84f21015b7dddc9484de19d0__COUNT_returns1"/>

## Returns

UNSIGNED BIGINT



<a name="loioa54290fd84f21015b7dddc9484de19d0__COUNT_remarks1"/>

## Remarks

Specifying COUNT \(\) is equivalent to specifying COUNT \( \* \).



<a name="loioa54290fd84f21015b7dddc9484de19d0__COUNT_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa54290fd84f21015b7dddc9484de19d0__iq_refbb_378"/>

## Example

Returns each unique city, and the number of rows with that city value:

```
SELECT city , Count(*)
FROM Employees
GROUP BY city
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[AVG Function \[Aggregate\] for Data Lake Relational Engine](avg-function-aggregate-for-data-lake-relational-engine-a535f04.md "Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.")

[SUM Function \[Aggregate\] for Data Lake Relational Engine](sum-function-aggregate-for-data-lake-relational-engine-a5889fe.md "Returns the total of the specified expression for each group of rows.")

[COUNT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/bd71ba2eab21415e8d3ce875005fc9b9.html "Counts the number of rows in a group, depending on the specified parameters.") :arrow_upper_right:

