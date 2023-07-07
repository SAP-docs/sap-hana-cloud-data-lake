<!-- loioa544131284f21015a70ed7c8e7db2f8b -->

# DATE Function \[Date and Time\] for Data Lake Relational Engine

Converts the expression into a date, and removes any hours, minutes, or seconds.



```
DATE ( <expression> )
```



<a name="loioa544131284f21015a70ed7c8e7db2f8b__DATE_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The value to be converted to date format. The expression is usually a string.



</dd>
</dl>



<a name="loioa544131284f21015a70ed7c8e7db2f8b__DATE_returns1"/>

## Returns

DATE



<a name="loioa544131284f21015a70ed7c8e7db2f8b__DATE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa544131284f21015a70ed7c8e7db2f8b__DATE_example1"/>

## Example

The following statement returns the value 1988-11-26 as a date:

```
SELECT DATE( '1988-11-26 21:20:53' ) FROM iq_dummy
```

**Related Information**  


[DATE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/e5839f4e21a9431984d1705f1691f2fa.html "Converts the expression into a date, and removes any hours, minutes, or seconds.") :arrow_upper_right:

