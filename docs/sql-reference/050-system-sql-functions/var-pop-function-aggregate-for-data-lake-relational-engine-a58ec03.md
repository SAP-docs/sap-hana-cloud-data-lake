<!-- loioa58ec03e84f21015b373c5236f4567a1 -->

# VAR\_POP Function \[Aggregate\] for Data Lake Relational Engine

Computes the statistical variance of a population consisting of a numeric-expression, as a `DOUBLE`.



```
VAR_POP ( [ ALL ] <expression> );
```



<a name="loioa58ec03e84f21015b373c5236f4567a1__VAR_POP_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression \(commonly a column name\) that has a population-based variance that is calculated over a set of rows.



</dd>
</dl>



<a name="loioa58ec03e84f21015b373c5236f4567a1__VAR_POP_returns1"/>

## Result Set

DOUBLE



<a name="loioa58ec03e84f21015b373c5236f4567a1__VAR_POP_remarks1"/>

## Remarks

Computes the population variance of the provided *<value expression\>* evaluated for each row of the group or partition \(if DISTINCT was specified, then each row that remains after duplicates have been eliminated\), defined as the sum of squares of the difference of *<value expression\>*, from the mean of *<value expression\>*, divided by the number of rows \(remaining\) in the group or partition.

Population-based variances are computed according to the following formula:

![Computes the population variance of the provided value expression evaluated for each row of the group or partition if DISTINCT was specified, then each row that remains after duplicates have been eliminated, defined as the sum of squares of the difference of value expression, from the mean of value expression, divided by the number of rows remaining in the group or partition](images/varpop_gif_a16ec8c.gif)



<a name="loioa58ec03e84f21015b373c5236f4567a1__VAR_POP_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58ec03e84f21015b373c5236f4567a1__VAR_POP_example1"/>

## Example

The following statement lists the average and variance in the number of items per order in different time periods:

```
SELECT year( ShipDate ) AS Year, quarter( ShipDate )
  AS Quarter, AVG( Quantity ) AS Average, 
  VAR_POP( Quantity ) AS Variance 
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

203.9021

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

225.8109

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

[VAR_POP Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/eb8e5a4d6b304dedab621a6bd58a471d.html "Computes the statistical variance of a population consisting of a numeric-expression, as a DOUBLE.") :arrow_upper_right:

