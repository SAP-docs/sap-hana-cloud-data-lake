<!-- loioa53996d784f21015a34086a244c40db1 -->

# CAST Function \[Data Type Conversion\] for Data Lake Relational Engine

Returns the value of an expression converted to a supplied data type.



```
CAST ( <expression> AS <data type> );
```



<a name="loioa53996d784f21015a34086a244c40db1__CAST_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression to be converted.



</dd><dt><b>

*<data type\>*

</b></dt>
<dd>

The data type to cast the expression into. Set the data type explicitly, or specify the %TYPE attribute to set the data type to the data type of a column in a table or view, or to the data type of a variable.



</dd>
</dl>



<a name="loioa53996d784f21015a34086a244c40db1__CAST_returns1"/>

## Result Set

The specified data type.



<a name="loioa53996d784f21015a34086a244c40db1__CAST_remarks1"/>

## Remarks

If you do not indicate a length for character string types, data lake Relational Engine chooses an appropriate length. If neither precision nor scale is specified for a DECIMAL conversion, the database server selects appropriate values.

In data lake Relational Engine, a timestamp data type column can support 6 or 7 decimal precision. See [TIMESTAMP Data Type Precision in Data Lake Relational Engine](../020-sql-data-types/timestamp-data-type-precision-in-data-lake-relational-engine-520ce6c.md). If you attempt to insert 7 decimal precision data into a 6 decimal precision column in the data lake Relational Engine, then the value will be truncated to 6 decimal places and precision is lost. To prevent this behavior, set the TIMESTAMP\_RTRUNCATION database option to ON. See [TIMESTAMP\_RTRUNCATION Option for Data Lake Relational Engine](../090-database-options/timestamp-rtruncation-option-for-data-lake-relational-engine-dbb08c7.md).When enabled, the CAST operation fails if precision will be lost on a timestamp column.

Set the data type explicitly, or specify the %TYPE attribute to set the data type to the data type of a column in a table or view, or to the data type of a variable. For example:

```
SELECT CAST( NULL AS NUMERIC ) A,
       CAST( NULL AS NUMERIC(15,2) ) B;
```

is described as:

```
A NUMERIC(1,0);
B NUMERIC(15,2);
```



<a name="loioa53996d784f21015a34086a244c40db1__CAST_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa53996d784f21015a34086a244c40db1__CAST_examples1"/>

## Examples

-   The following function ensures a string is used as a date:

    ```
    CAST( '2000-10-31' AS DATE );
    ```

-   The following is the value of the expression `1 + 2`. The data type to cast the expression into. Set the data type is calculated, and the result cast into a single-character string, the length the data server assigns:

    ```
    CAST( 1 + 2 AS CHAR );
    ```

-   You can use the `CAST` function to shorten strings:

    ```
    SELECT CAST( lname AS CHAR(5) ) FROM Customers;
    ```


**Related Information**  


[TIMESTAMP Data Type Precision in Data Lake Relational Engine](../020-sql-data-types/timestamp-data-type-precision-in-data-lake-relational-engine-520ce6c.md "Precision conflicts between TIMESTAMP data types result in data loss.")

[GRAPHICAL\_PLAN Function \[String\] for Data Lake Relational Engine](graphical-plan-function-string-for-data-lake-relational-engine-a553c53.md "Returns the graphical query plan to Interactive SQL in an XML format string.")

[DAYS Function \[Date and Time\] for Data Lake Relational Engine](days-function-date-and-time-for-data-lake-relational-engine-a54a45b.md "Returns the number of days since an arbitrary starting date, returns the number of days between two specified dates, or adds the specified integer-expression number of days to a given date.")

[CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine](convert-function-data-type-conversion-for-data-lake-relational-engine-a53f6ef.md "Returns an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[TIMESTAMP_RTRUNCATION Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/7ea796c77e5047c78acff41829be70aa.html "Controls whether INSERT, UPDATE, or CAST operations on TIMESTAMP data type columns fails if loss of precision will result.") :arrow_upper_right:

[CAST Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/4a2c75bbed1d4b399e51f704ee7d35dc.html "Returns the value of an expression converted to a supplied data type.") :arrow_upper_right:

