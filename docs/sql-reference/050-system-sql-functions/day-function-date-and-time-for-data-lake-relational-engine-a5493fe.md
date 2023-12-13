<!-- loioa5493fe284f2101587fac052951c6f01 -->

# DAY Function \[Date and Time\] for Data Lake Relational Engine

Returns an integer from 1 to 31 corresponding to the day of the month of the date specified.



```
DAY ( <date-expression> );
```



<a name="loioa5493fe284f2101587fac052951c6f01__DAY_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date.



</dd>
</dl>



<a name="loioa5493fe284f2101587fac052951c6f01__DAY_returns1"/>

## Result Set

SMALLINT



<a name="loioa5493fe284f2101587fac052951c6f01__DAY_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5493fe284f2101587fac052951c6f01__DAY_example1"/>

## Example

The following statement returns the value 12:

```
SELECT DAY( '2001-09-12' ) FROM iq_dummy;
```

**Related Information**  


[DAY Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/ff00ee7be6544c12a1e279a814961857.html "Returns an integer from 1 to 31 corresponding to the day of the month of the date specified.") :arrow_upper_right:

