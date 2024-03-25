<!-- loioa5449deb84f210159a75e748a099539f -->

# DATEADD Function \[Date and Time\] for Data Lake Relational Engine

Returns the date produced by adding the specified number of the specified date parts to a date.



```
DATEADD ( <date-part>, <numeric-expression>, <date-expression> );
```



<a name="loioa5449deb84f210159a75e748a099539f__DATEADD_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be added to the date.



</dd><dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number of date parts to be added to the date. *<numeric-expression\>* can be any numeric type; the value is truncated to an integer. The maximum microsecond in *<numeric-expression\>* is 2147483647, that is, 35:47.483647 \(35 minutes 47 seconds 483647 microseconds\).



</dd><dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date expression in the format `{ date | time | timestamp }`.



</dd>
</dl>



<a name="loioa5449deb84f210159a75e748a099539f__DATEADD_retunrs1"/>

## Result Set

The result type is based on the *<date\_expression\>* type.



<a name="loioa5449deb84f210159a75e748a099539f__DATEADD_remarks1"/>

## Remarks

DATEADD is a Transact-SQL compatible data manipulation function.



<a name="loioa5449deb84f210159a75e748a099539f__DATEADD_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa5449deb84f210159a75e748a099539f__DATEADD_examles1"/>

## Examples

-   The following statement returns the value 1995-11-02 00:00:00.000:

    ```
    SELECT DATEADD( MONTH, 102, '1987/05/02' ) FROM iq_dummy;
    ```

-   The following statement returns the value 2009-11-10 14:57:52.722016:

    ```
    SELECT DATEADD(MICROSECOND, 15, '2009-11-10
    14:57:52.722001') FROM iq_dummy;
    ```

-   The following statement returns the value 1985-05-02 00:00:00.123456:

    ```
    SELECT DATEADD(MICROSECOND, 123456, '1985/05/02')
    FROM iq_dummy;
    ```

-   The following statement returns the value 1985-05-01 23:59:59.876544:

    ```
    SELECT DATEADD(MICROSECOND, -123456, '1985/05/02')
    FROM iq_dummy;
    ```

-   The following statement returns the value 2009-11-03 11:10:42.033192:

    ```
    SELECT DATEADD(MCS, 2, '2009-11-03 11:10:42.033190')
    FROM iq_dummy;
    ```


**Related Information**  


[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.")

[DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine](datediff-function-date-and-time-for-data-lake-relational-engine-a545a63.md "Returns the interval between two dates.")

[DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md "Calculates a new date, time, or datetime value by reducing the provided value down to the nearest lower value of the specified multiple with the specified granularity.")

[DATENAME Function \[Date and Time\] for Data Lake Relational Engine](datename-function-date-and-time-for-data-lake-relational-engine-a5472b7.md "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.")

[DATEPART Function \[Date and Time\] for Data Lake Relational Engine](datepart-function-date-and-time-for-data-lake-relational-engine-a547b06.md "Returns an integer value for the specified part of a date/time value.")

[DATEROUND Function \[Date and Time\] for Data Lake Relational Engine](dateround-function-date-and-time-for-data-lake-relational-engine-a5483a3.md "Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.")

[Date Parts in Data Lake Relational Engine](date-parts-in-data-lake-relational-engine-a52b8dd.md "Many of the date functions use dates built from date parts.")

[DATEADD Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/202015428c2c49239a2aec8d572a0613.html "Returns the date produced by adding the specified number of the specified date parts to a date.") :arrow_upper_right:

