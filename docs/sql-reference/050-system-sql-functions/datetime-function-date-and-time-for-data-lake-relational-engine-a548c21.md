<!-- loioa548c21f84f210158350cf2fab822610 -->

# DATETIME Function \[Date and Time\] for Data Lake Relational Engine

Converts an expression into a timestamp.



```
DATETIME ( <expression> );
```



<a name="loioa548c21f84f210158350cf2fab822610__DATETIME_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression to be converted. The expression is usually a string. Conversion errors may be reported.



</dd>
</dl>



<a name="loioa548c21f84f210158350cf2fab822610__DATETIME_returns1"/>

## Result Set

TIMESTAMP



<a name="loioa548c21f84f210158350cf2fab822610__DATETIME_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa548c21f84f210158350cf2fab822610__DATETIME_examples1"/>

## Example

The following statement returns a timestamp with value 1998-09-09 12:12:12.000:

```
SELECT DATETIME( '1998-09-09 12:12:12.000' ) FROM iq_dummy;
```

**Related Information**  


[DATETIME Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/87c2ebfc15364ff0b9b4e7dc0fa66207.html "Converts an expression into a timestamp.") :arrow_upper_right:

