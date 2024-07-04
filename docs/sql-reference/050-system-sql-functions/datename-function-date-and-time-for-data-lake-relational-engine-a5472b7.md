<!-- loioa5472b7084f21015892b91f8f67b6ef9 -->

# DATENAME Function \[Date and Time\] for Data Lake Relational Engine

Returns the name of the specified part \(such as the month “June”\) of a date/time value, as a character string.



```
DATEMNAME ( <date-part>, <date-expression> );
```



<a name="loioa5472b7084f21015892b91f8f67b6ef9__DATENAME_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be named.



</dd><dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date for which the date part name is to be returned. The date must contain the requested date-part.



</dd>
</dl>



<a name="loioa5472b7084f21015892b91f8f67b6ef9__DATENAME_returns1"/>

## Result Set

VARCHAR



<a name="loioa5472b7084f21015892b91f8f67b6ef9__DATENAME_remarks1"/>

## Remarks

`DATENAME` returns a character string, even if the result is numeric, such as 23, for the day.



<a name="loioa5472b7084f21015892b91f8f67b6ef9__DATENAME_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa5472b7084f21015892b91f8f67b6ef9__DATENAME_examples1"/>

## Examples

-   The following statement returns the value May:

    ```
    SELECT DATENAME( MONTH , '1987/05/02' )
    FROM iq_dummy;
    ```

-   The following statement returns the value 722,001:

    ```
    SELECT DATENAME(MICROSECOND, '2009-11-10
    14:57:52.722001') FROM iq_dummy;
    ```

-   The following statement returns the value 777,777:

    ```
    SELECT DATENAME(MICROSECOND, '2000/07/07
    07:07:07.777777') FROM iq_dummy;
    ```

-   The following statement returns the value 33,189:

    ```
    SELECT DATENAME(MCS, '2009-11-03 11:10:42.033189')
    FROM iq_dummy;
    ```


**Related Information**  


[DATEADD Function \[Date and Time\] for Data Lake Relational Engine](dateadd-function-date-and-time-for-data-lake-relational-engine-a5449de.md "Returns the date produced by adding the specified number of the specified date parts to a date.")

[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.")

[DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine](datediff-function-date-and-time-for-data-lake-relational-engine-a545a63.md "Returns the interval between two dates.")

[DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md "Calculates a new date, time, or datetime value by reducing the provided value down to the nearest lower value of the specified multiple with the specified granularity.")

[DATEPART Function \[Date and Time\] for Data Lake Relational Engine](datepart-function-date-and-time-for-data-lake-relational-engine-a547b06.md "Returns an integer value for the specified part of a date/time value.")

[DATEROUND Function \[Date and Time\] for Data Lake Relational Engine](dateround-function-date-and-time-for-data-lake-relational-engine-a5483a3.md "Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.")

[Date Parts in Data Lake Relational Engine](date-parts-in-data-lake-relational-engine-a52b8dd.md "Many of the date functions use dates built from date parts.")

[DATENAME Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/b6977f358a8549aab30b4f2c48dd3c83.html "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.") :arrow_upper_right:

