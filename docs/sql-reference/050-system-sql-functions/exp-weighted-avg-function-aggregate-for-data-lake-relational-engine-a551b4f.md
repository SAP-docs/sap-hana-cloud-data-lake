<!-- loioa551b4fb84f210158a07f463ff01b5e2 -->

# EXP\_WEIGHTED\_AVG Function \[Aggregate\] for Data Lake Relational Engine

Calculates an exponential weighted moving average. Weightings determine the relative importance of each quantity that makes up the average.



```
EXP_WEIGHTED_AVG (<expression>, <period-expression>)
                OVER (<window-spec>);
```



<a name="loioa551b4fb84f210158a07f463ff01b5e2__EXP_WEIGHTED_AVG_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

A numeric expression for which a weighted value is being computed.



</dd><dt><b>

*<period-expression\>*

</b></dt>
<dd>

A numeric expression specifying the period for which the average is to be computed.



</dd><dt><b>

*<window-spec\>*

</b></dt>
<dd>

Specified when using this function as a window function.



</dd>
</dl>



<a name="loioa551b4fb84f210158a07f463ff01b5e2__EXP_WEIGHTED_AVG_remarks1"/>

## Remarks

Similar to the WEIGHTED\_AVG function, the weights in EXP\_WEIGHTED\_AVG decrease over time. However, weights in WEIGHTED\_AVG decrease arithmetically, whereas weights in EXP\_WEIGHTED\_AVG decrease exponentially. Exponential weighting applies more weight to the most recent values, and decreases the weight for older values while still applying some weight.

Data lake Relational Engine calculates the exponential moving average using:

```
S*C+(1-S)*PEMA
```

In the calculation above, data lake Relational Engine applies the smoothing factor by multiplying the current closing price \(C\) by the smoothing constant \(S\) added to the product of the previous day’s exponential moving average value \(PEMA\) and 1 minus the smoothing factor.

Data lake Relational Engine calculates the exponential moving average over the entire period specified by the OVER clause. *<period-expression\>* specifies the moving range of the exponential moving average.

The *<window-spec\>* parameter represents usage as a window function in a `SELECT` statement. As such, you can specify elements of *<window-spec\>* either in the function syntax \(inline\), or with a `WINDOW` clause in the `SELECT` statement. The *<window-spec\>* must contain an `ORDER BY` statement and cannot contain a frame specification.

> ### Note:  
> ROLLUP and CUBE are not supported in the GROUP BY clause. DISTINCT is not supported.



<a name="loioa551b4fb84f210158a07f463ff01b5e2__EXP_WEIGHTED_AVG_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa551b4fb84f210158a07f463ff01b5e2__EXP_WEIGHTED_AVG_examples1"/>

## Examples

The following example returns an exponential weighted average of salaries for employees in Florida with the salary of recently hired employees contributing the most weight to the average. There are three rows used in the weighting:

```
SELECT DepartmentID, Surname, Salary, EXP_WEIGHTED_AVG(Salary, 3) 
                    OVER (ORDER BY YEAR(StartDate) DESC) as "W_AVG" FROM Employees
                    WHERE State IN ('FL') ORDER BY StartDate DESC;
```

The returned result set is:


<table>
<tr>
<th valign="top">

DepartmentID

</th>
<th valign="top">

Surname

</th>
<th valign="top">

Salary

</th>
<th valign="top">

W\_AVG

</th>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Evans

</td>
<td valign="top">

68,940.000

</td>
<td valign="top">

34,470.000000

</td>
</tr>
<tr>
<td valign="top">

300

</td>
<td valign="top">

Litton

</td>
<td valign="top">

58,930.000

</td>
<td valign="top">

46,700.000000

</td>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Sterling

</td>
<td valign="top">

64,900.000

</td>
<td valign="top">

55,800.000000

</td>
</tr>
<tr>
<td valign="top">

200

</td>
<td valign="top">

Kelly

</td>
<td valign="top">

87,500.000

</td>
<td valign="top">

71,650.000000

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Charlton

</td>
<td valign="top">

28,300.000

</td>
<td valign="top">

49,975.000000

</td>
</tr>
<tr>
<td valign="top">

100

</td>
<td valign="top">

Lull

</td>
<td valign="top">

87,900.000

</td>
<td valign="top">

68,937.500000

</td>
</tr>
<tr>
<td valign="top">

100

</td>
<td valign="top">

Gowda

</td>
<td valign="top">

59,840.000

</td>
<td valign="top">

60,621.875000

</td>
</tr>
<tr>
<td valign="top">

400

</td>
<td valign="top">

Francis

</td>
<td valign="top">

53,870.000

</td>
<td valign="top">

61,403.750000

</td>
</tr>
</table>

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[WEIGHTED\_AVG Function \[Aggregate\] for Data Lake Relational Engine](weighted-avg-function-aggregate-for-data-lake-relational-engine-a590e30.md "Calculates an arithmetically (or linearly) weighted average.")

[EXP_WEIGHTED_AVG Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/ac831a074ab343628271364a30d557bf.html "Calculates an exponential weighted moving average. Weightings determine the relative importance of each quantity that makes up the average.") :arrow_upper_right:

