<!-- loioa58f41a384f2101582a6bccb68243889 -->

# VAR\_SAMP Function \[Aggregate\] for Data Lake Relational Engine

Computes the statistical variance of a sample consisting of a numeric-expression, as a `DOUBLE`.



```
VAR_SAMP ( [ ALL ] <expression> );
```



<a name="loioa58f41a384f2101582a6bccb68243889__VAR_SAMP_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression \(commonly a column name\) that has a sample-based variance that is calculated over a set of rows.



</dd>
</dl>



<a name="loioa58f41a384f2101582a6bccb68243889__VAR_SAMP_returns1"/>

## Result Set

DOUBLE



<a name="loioa58f41a384f2101582a6bccb68243889__VAR_SAMP_remarks1"/>

## Remarks

> ### Note:  
> `VAR_SAMP` is an alias of `VARIANCE`.

Computes the sample variance of *<value expression\>* evaluated for each row of the group or partition \(if DISTINCT was specified, then each row that remains after duplicates have been eliminated\), defined as the sum of squares of the difference of *<value expression\>*, from the mean of *<value expression\>*, divided by one less than the number of rows \(remaining\) in the group or partition.

NULL returns NULL for a one-element input set in data lake Relational Engine.

Variances are computed according to the following formula, which assumes a normal distribution:

![Computes the sample variance of value expression evaluated for each row of the group or partition  if DISTINCT was specified, then each row that remains after duplicates have been eliminated, defined as the sum of squares of the difference of value expression, from the mean of value expression, divided by one less than the number of rows remaining in the group or partition](images/varpop_gif_a16ec8c.gif)



<a name="loioa58f41a384f2101582a6bccb68243889__VAR_SAMP_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58f41a384f2101582a6bccb68243889__VAR_SAMP_example1"/>

## Example

The following statement lists the average and variance in the number of items per order in different time periods:

```
SELECT year( ShipDate ) AS Year, quarter( ShipDate )
  AS Quarter, AVG( Quantity ) AS Average,  
  VAR_SAMP( Quantity ) AS Variance 
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

205.1158

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

227.0939

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

[VAR_SAMP Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/4e77eae4118f432c95bd09f867eb3f06.html "Computes the statistical variance of a sample consisting of a numeric-expression, as a DOUBLE.") :arrow_upper_right:

