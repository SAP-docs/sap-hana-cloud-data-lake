<!-- loioa549c43b84f21015a569d8e52c4af3f8 -->

# DAYNAME Function \[Date and Time\] for Data Lake Relational Engine

Returns the name of the day of the week from the specified date.



```
DAYNAME ( <date-expression> );
```



<a name="loioa549c43b84f21015a569d8e52c4af3f8__DAYNAME_parameters1"/>

## Parameters


<dl>
<dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date.



</dd>
</dl>



<a name="loioa549c43b84f21015a569d8e52c4af3f8__DAYNAME_returns1"/>

## Result Set

VARCHAR



<a name="loioa549c43b84f21015a569d8e52c4af3f8__DAYNAME_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa549c43b84f21015a569d8e52c4af3f8__DAYNAME_example1"/>

## Example

The following statement returns the value Saturday:

```
SELECT DAYNAME ( '1987/05/02' ) FROM iq_dummy;
```

**Related Information**  


[DAYNAME Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/be690a0aa62c4e67986070c70f25b3fe.html "Returns the name of the day of the week from the specified date.") :arrow_upper_right:

