<!-- loioa55651ad84f210158eceac6470043938 -->

# HOUR Function \[Date and Time\] for Data Lake Relational Engine

Returns a number from 0 to 23 corresponding to the hour component of the specified date/time.



```
HOUR ( <datetime-expression> );
```



<a name="loioa55651ad84f210158eceac6470043938__HOUR_parm1"/>

## Parameters


<dl>
<dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date/time.



</dd>
</dl>



<a name="loioa55651ad84f210158eceac6470043938__HOUR_returns1"/>

## Result Set

SMALLINT



<a name="loioa55651ad84f210158eceac6470043938__HOUR_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55651ad84f210158eceac6470043938__HOUR_example1"/>

## Examples

The following statement returns the value 21:

```
SELECT HOUR( '1998-07-09 21:12:13' ) FROM iq_dummy;
```

**Related Information**  


[HOUR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/13ca8f80a24a45b3ae7e434753dd97c8.html "Returns a number from 0 to 23 corresponding to the hour component of the specified date/time.") :arrow_upper_right:

