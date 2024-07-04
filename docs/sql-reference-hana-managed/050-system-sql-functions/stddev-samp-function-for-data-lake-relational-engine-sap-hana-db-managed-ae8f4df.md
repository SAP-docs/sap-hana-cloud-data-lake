<!-- loioae8f4df1cf8d477e881f9e3360210ae0 -->

# STDDEV\_SAMP Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the standard deviation of a sample consisting of a numeric-expression, as a `DOUBLE`.



```
STDDEV_SAMP ( [ ALL ] <expression> );
```



<a name="loioae8f4df1cf8d477e881f9e3360210ae0__section_ery_p43_wrb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression \(commonly a column name\) whose sample-based standard deviation is calculated over a set of rows.



</dd>
</dl>



<a name="loioae8f4df1cf8d477e881f9e3360210ae0__section_uvp_j55_vrb"/>

## Result Set

DOUBLE



<a name="loioae8f4df1cf8d477e881f9e3360210ae0__section_kb1_k55_vrb"/>

## Remarks

> ### Note:  
> `STDDEV_SAMP` is an alias for `STDDEV`.

Computes the sample standard deviation of the provided *<value expression\>* evaluated for each row of the group or partition \(if DISTINCT was specified, then each row that remains after duplicates have been eliminated\), defined as the square root of the sample variance.

NULL returns NULL for a one-element input set.

Standard deviations are computed according to the following formula, which assumes a normal distribution:

![Computes the sample standard deviation of the provided value expression evaluated for each row of the group or partition if DISTINCT was specified, then each row that remains after duplicates have been eliminated, defined as the square root of the sample variance](images/stdsamp_gif_a16e33a.gif)



<a name="loioae8f4df1cf8d477e881f9e3360210ae0__section_pnh_r43_wrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioae8f4df1cf8d477e881f9e3360210ae0__section_mrg_l55_vrb"/>

## Examples

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


[STDDEV_SAMP Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a584728f84f210158226d1181b68d335.html "Computes the standard deviation of a sample consisting of a numeric-expression, as a DOUBLE.") :arrow_upper_right:

