<!-- loiob6d0deaed8aa424a88f56de678b77b77 -->

# QUARTERSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number indicating the quarter of the year from the supplied date expression and quarter start month.



```
QUARTERSTR( <date-expression>,[ <quarter_start_month> ] );
```



<a name="loiob6d0deaed8aa424a88f56de678b77b77__section_dcy_ln5_vrb"/>

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



<a name="loiob6d0deaed8aa424a88f56de678b77b77__section_mvn_mn5_vrb"/>

## Result Set

A string in the format YYYY-QN where YYYY is year and N is quarter number.



<a name="loiob6d0deaed8aa424a88f56de678b77b77__section_w2b_nn5_vrb"/>

## Standards and Compatibility

-   Nonstandard function.



<a name="loiob6d0deaed8aa424a88f56de678b77b77__section_p2s_nn5_vrb"/>

## Example

With the `DATE_ORDER` option set to the default of *<ymd\>*, the following statement returns the value 1998-Q4:

```
SELECT QUARTERSTR ( '1999/01/28', 2 ) FROM iq_dummy;
```

**Related Information**  


[QUARTERSTR Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/8fbd6b73408a49d1aa5c88d99954bf7c.html "Returns a number indicating the quarter of the year from the supplied date expression and quarter start month.") :arrow_upper_right:

