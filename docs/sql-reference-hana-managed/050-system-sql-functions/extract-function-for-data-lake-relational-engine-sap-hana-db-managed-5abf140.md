<!-- loio5abf14024b6949cd9539ee8467acfb10 -->

# EXTRACT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a date part from a DATE, TIME, or TIMESTAMP expression.



```
EXTRACT( <date-part> FROM <timestamp-expression> );
```



<a name="loio5abf14024b6949cd9539ee8467acfb10__section_rgj_xpd_gsb"/>

## Parameters


<dl>
<dt><b>

*<date-part\>* 

</b></dt>
<dd>

The date part to be returned. The valid values are YEAR, MONTH, DAY, HOUR, MINUTE, and SECOND.



</dd><dt><b>

*<timestamp-expression\>* 

</b></dt>
<dd>

The DATE, TIME, or TIMESTAMP value.



</dd>
</dl>



<a name="loio5abf14024b6949cd9539ee8467acfb10__section_qn4_ypd_gsb"/>

## Result Set

If *<date-part\>* is SECOND, then the function returns a string that includes a 7-digit fractional second \(and up to 100-nanosecond accuracy if the date/time datatype supports it\). For all other *<date-part\>* values, the function returns an INTEGER value.



<a name="loio5abf14024b6949cd9539ee8467acfb10__section_kzf_zpd_gsb"/>

## Remarks

The EXTRACT function is similar to the DATEPART function but not completely. The EXTRACT function accepts only a subset of date parts permitted with the DATEPART function. Also, the two functions return different values when *<date-part\>* is SECOND.

Date parts YY, MM, DD, HH, MI, SS, TZH, and TZM may also be used but do not conform to the SQL Standard.



## Example

The following statement returns 56:

```
SELECT EXTRACT( SECOND FROM '2021-07-01 12:34:56.345678' ) FROM iq_dummy;
```

The following statement returns 7:

```
SELECT EXTRACT( MONTH FROM '2021-07-01 12:34:56.345678' ) FROM iq_dummy;
```

The following statement returns 2021:

```
SELECT EXTRACT( YEAR FROM '21-07-01 12:34:56.345678' ) FROM iq_dummy;
```

It does so since 21-07-01 represents July 1, 2021.

**Related Information**  


[EXTRACT Function \[Date and Time\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/c3565b1366b448828db3cc916507f15b.html "Returns a date part from a DATE, TIME, or TIMESTAMP expression.") :arrow_upper_right:

