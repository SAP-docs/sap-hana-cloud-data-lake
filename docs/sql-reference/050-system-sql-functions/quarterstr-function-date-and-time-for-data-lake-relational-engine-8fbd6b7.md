<!-- loio8fbd6b73408a49d1aa5c88d99954bf7c -->

# QUARTERSTR Function \[Date and Time\] for Data Lake Relational Engine

Returns a number indicating the quarter of the year from the supplied date expression and quarter start month.



```
QUARTERSTR( <date-expression>,[ <quarter_start_month> ] );
```



<a name="loio8fbd6b73408a49d1aa5c88d99954bf7c__QUARTERSTR_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

A date.



</dd><dt><b>

*<quarter\_start\_month\>*

</b></dt>
<dd>

Any integer 1 to 12. If not specified, default value is 1 \(January\).



</dd>
</dl>



<a name="loio8fbd6b73408a49d1aa5c88d99954bf7c__QUARTERSTR_returns1"/>

## Result Set

A string in the format YYYY-QN where YYYY is year and N is quarter number.



<a name="loio8fbd6b73408a49d1aa5c88d99954bf7c__QUARTERSTR_standards1"/>

## Standards and Compatibility

-   Nonstandard function.



<a name="loio8fbd6b73408a49d1aa5c88d99954bf7c__QUARTERSTR_examples1"/>

## Example

With the `DATE_ORDER` option set to the default of *<ymd\>*, the following statement returns the value 1998-Q4:

```
SELECT QUARTERSTR ( '1999/01/28', 2 ) FROM iq_dummy;
```

**Related Information**  


[QUARTERSTR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b6d0deaed8aa424a88f56de678b77b77.html "Returns a number indicating the quarter of the year from the supplied date expression and quarter start month.") :arrow_upper_right:

