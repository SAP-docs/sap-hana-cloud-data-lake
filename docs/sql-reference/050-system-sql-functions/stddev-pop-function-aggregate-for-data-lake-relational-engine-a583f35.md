<!-- loioa583f35984f21015b952ffc0a8c12597 -->

# STDDEV\_POP Function \[Aggregate\] for Data Lake Relational Engine

Computes the standard deviation of a population consisting of a numeric-expression, as a `DOUBLE`.



```
STDDEV_POP ( [ ALL ] <expression> );
```



<a name="loioa583f35984f21015b952ffc0a8c12597__STDDEV_POP_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression \(commonly a column name\) that has a population-based standard deviation that is calculated over a set of rows.



</dd>
</dl>



<a name="loioa583f35984f21015b952ffc0a8c12597__STDDEV_POP_returns1"/>

## Result Set

DOUBLE



<a name="loioa583f35984f21015b952ffc0a8c12597__STDDEV_POP_remarks1"/>

## Remarks

Computes the population standard deviation of the provided *<value expression\>* evaluated for each row of the group or partition \(if DISTINCT was specified, then each row that remains after duplicates have been eliminated\), defined as the square root of the population variance.

![Computes the population standard deviation of the provided value expression evaluated for each row of the group or partition if DISTINCT was specified, then each row that remains after duplicates have been eliminated, defined as the square root of the population variance](images/stdpop_gif_a16d7b7.gif)



<a name="loioa583f35984f21015b952ffc0a8c12597__STDDEV_POP_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa583f35984f21015b952ffc0a8c12597__STDDEV_POP_example1"/>

## Example

The following statement lists the average and variance in the number of items per order in different time periods:

```
SELECT year( ship_date ) AS Year, quarter( ship_date )
  AS Quarter, AVG( quantity ) AS Average, 
  STDDEV_POP ( quantity ) AS Variance 
FROM SalesOrderItems GROUP BY Year, Quarter 
  ORDER BY Year, Quarter;
```


<table>
<tr>
<th valign="top" rowspan="1">

Year

</th>
<th valign="top" rowspan="1">

Quarter

</th>
<th valign="top" rowspan="1">

Average

</th>
<th valign="top" rowspan="1">

Variance

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

2000

</td>
<td valign="top" rowspan="1">

1

</td>
<td valign="top" rowspan="1">

25.775148

</td>
<td valign="top" rowspan="1">

14.2794

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

2000

</td>
<td valign="top" rowspan="1">

2

</td>
<td valign="top" rowspan="1">

27.050847

</td>
<td valign="top" rowspan="1">

15.0270

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

...

</td>
<td valign="top" rowspan="1">

...

</td>
<td valign="top" rowspan="1">

...

</td>
<td valign="top" rowspan="1">

...

</td>
</tr>
</table>

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[STDDEV_POP Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b943ce2c21964c07baa10bd8d387f972.html "Computes the standard deviation of a population consisting of a numeric-expression, as a DOUBLE.") :arrow_upper_right:

