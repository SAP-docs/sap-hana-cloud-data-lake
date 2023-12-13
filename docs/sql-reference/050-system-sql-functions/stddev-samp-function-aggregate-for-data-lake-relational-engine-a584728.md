<!-- loioa584728f84f210158226d1181b68d335 -->

# STDDEV\_SAMP Function \[Aggregate\] for Data Lake Relational Engine

Computes the standard deviation of a sample consisting of a numeric-expression, as a `DOUBLE`.



```
STDDEV_SAMP ( [ ALL ] <expression> );
```



<a name="loioa584728f84f210158226d1181b68d335__STDDEV_SAMP_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression \(commonly a column name\) whose sample-based standard deviation is calculated over a set of rows.



</dd>
</dl>



<a name="loioa584728f84f210158226d1181b68d335__STDDEV_SAMP_returns1"/>

## Result Set

DOUBLE



<a name="loioa584728f84f210158226d1181b68d335__STDDEV_SAMP_remarks1"/>

## Remarks

> ### Note:  
> `STDDEV_SAMP` is an alias for `STDDEV`.

Computes the sample standard deviation of the provided *<value expression\>* evaluated for each row of the group or partition \(if DISTINCT was specified, then each row that remains after duplicates have been eliminated\), defined as the square root of the sample variance.

NULL returns NULL for a one-element input set.

Standard deviations are computed according to the following formula, which assumes a normal distribution:

![Computes the sample standard deviation of the provided value expression evaluated for each row of the group or partition if DISTINCT was specified, then each row that remains after duplicates have been eliminated, defined as the square root of the sample variance](images/stdsamp_gif_a16e33a.gif)



<a name="loioa584728f84f210158226d1181b68d335__STDDEV_SAMP_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa584728f84f210158226d1181b68d335__STDDEV_SAMP_example1"/>

## Example

The following statement lists the average and variance in the number of items per order in different time periods:

```
SELECT year( ship_date ) AS Year, quarter( ship_date )
  AS Quarter, AVG( quantity ) AS Average, 
  STDDEV_SAMP( quantity ) AS Variance 
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

14.3218

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

15.0696

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

[STDDEV_SAMP Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/ae8f4df1cf8d477e881f9e3360210ae0.html "Computes the standard deviation of a sample consisting of a numeric-expression, as a DOUBLE.") :arrow_upper_right:

