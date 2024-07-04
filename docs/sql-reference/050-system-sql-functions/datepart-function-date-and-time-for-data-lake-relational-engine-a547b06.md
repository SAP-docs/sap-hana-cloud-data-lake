<!-- loioa547b06f84f210158ab3bd499f292d99 -->

# DATEPART Function \[Date and Time\] for Data Lake Relational Engine

Returns an integer value for the specified part of a date/time value.



```
DATEPART ( <date-part>, <date-expression> );
```



<a name="loioa547b06f84f210158ab3bd499f292d99__DATEPART_parm1"/>

## Parameters


<dl>
<dt><b>

*<date-part\>*

</b></dt>
<dd>

The date part to be returned.



</dd><dt><b>

*<date-expression\>*

</b></dt>
<dd>

The date for which the part is to be returned. The date must contain the date-part field.



</dd>
</dl>



<a name="loioa547b06f84f210158ab3bd499f292d99__DATEPART_returns1"/>

## Result Set

INT



<a name="loioa547b06f84f210158ab3bd499f292d99__DATEPART_remarks1"/>

## Remarks

The DATE, TIME, and DTTM indexes do not support some date parts \(Calyearofweek, Calweekofyear, Caldayofweek, Dayofyear, Millisecond, Microsecond\).



<a name="loioa547b06f84f210158ab3bd499f292d99__DATEPART_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa547b06f84f210158ab3bd499f292d99__DATEPART_example1"/>

## Examples

-   The following statement returns the value 5:

    ```
    SELECT DATEPART( MONTH, '1987/05/02' )
    FROM iq_dummy;
    ```

-   The following statement returns the value 722,001:

    ```
    SELECT DATEPART(MICROSECOND, '2009-11-10
    14:57:52.722001') FROM iq_dummy;
    ```

-   The following statement returns the value 777,777:

    ```
    SELECT DATEPART(MICROSECOND, '2000/07/07
    07:07:07.777777') FROM iq_dummy;
    ```

-   The following statement returns the value 33,189:

    ```
    SELECT DATEPART(MCS, '2009-11-03 11:10:42.033189')
    FROM iq_dummy;
    ```


**Related Information**  


[DATEADD Function \[Date and Time\] for Data Lake Relational Engine](dateadd-function-date-and-time-for-data-lake-relational-engine-a5449de.md "Returns the date produced by adding the specified number of the specified date parts to a date.")

[DATECEILING Function \[Date and Time\] for Data Lake Relational Engine](dateceiling-function-date-and-time-for-data-lake-relational-engine-a545210.md "Calculates a new date, time, or datetime value by increasing the provided value up to the nearest larger value of the specified granularity.")

[DATEDIFF Function \[Date and Time\] for Data Lake Relational Engine](datediff-function-date-and-time-for-data-lake-relational-engine-a545a63.md "Returns the interval between two dates.")

[DATEFLOOR Function \[Date and Time\] for Data Lake Relational Engine](datefloor-function-date-and-time-for-data-lake-relational-engine-a5462b6.md "Calculates a new date, time, or datetime value by reducing the provided value down to the nearest lower value of the specified multiple with the specified granularity.")

[DATENAME Function \[Date and Time\] for Data Lake Relational Engine](datename-function-date-and-time-for-data-lake-relational-engine-a5472b7.md "Returns the name of the specified part (such as the month “June”) of a date/time value, as a character string.")

[DATEROUND Function \[Date and Time\] for Data Lake Relational Engine](dateround-function-date-and-time-for-data-lake-relational-engine-a5483a3.md "Calculates a new date, time, or datetime value by rounding the provided value up or down to the nearest multiple of the specified value with the specified granularity.")

[Date Parts in Data Lake Relational Engine](date-parts-in-data-lake-relational-engine-a52b8dd.md "Many of the date functions use dates built from date parts.")

[DATEPART Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/a07008d5cbc347329b60d52b3e243ed6.html "Returns an integer value for the specified part of a date/time value.") :arrow_upper_right:

