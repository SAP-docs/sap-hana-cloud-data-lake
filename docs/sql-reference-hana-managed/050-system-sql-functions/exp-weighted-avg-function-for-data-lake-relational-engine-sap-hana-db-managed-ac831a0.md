<!-- loioac831a074ab343628271364a30d557bf -->

# EXP\_WEIGHTED\_AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Calculates an exponential weighted moving average. Weightings determine the relative importance of each quantity that makes up the average.



```
EXP_WEIGHTED_AVG (<expression>, <period-expression>)
                OVER (<window-spec>);
```



<a name="loioac831a074ab343628271364a30d557bf__section_asg_5rg_trb"/>

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



<a name="loioac831a074ab343628271364a30d557bf__section_tvs_5rg_trb"/>

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



<a name="loioac831a074ab343628271364a30d557bf__section_olr_vrg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[WINDOW Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/window-clause-for-data-lake-relational-engine-sap-hana-db-managed-c83b61b.md "Defines all or part of a window for use with window functions such as AVG and RANK in a SELECT statement.")

[WEIGHTED\_AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](weighted-avg-function-for-data-lake-relational-engine-sap-hana-db-managed-7a370d0.md "Calculates an arithmetically (or linearly) weighted average.")

[EXP_WEIGHTED_AVG Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a551b4fb84f210158a07f463ff01b5e2.html "Calculates an exponential weighted moving average. Weightings determine the relative importance of each quantity that makes up the average.") :arrow_upper_right:

