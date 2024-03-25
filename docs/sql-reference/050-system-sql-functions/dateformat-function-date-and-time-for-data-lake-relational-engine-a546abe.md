<!-- loioa546abe884f21015bc048c3994136804 -->

# DATEFORMAT Function \[Date and Time\] for Data Lake Relational Engine

Returns a string representing a date expression in the specified format.



```
DATEFORMAT ( <datetime-expression>, <string-expression> );
```



<a name="loioa546abe884f21015bc048c3994136804__DATEFORMAT_parm1"/>

## Parameters


<dl>
<dt><b>

*<datetime-expression\>*

</b></dt>
<dd>

The date and time to be converted, in the form of a date, time, timestamp, or character string.



</dd><dt><b>

*<string-expression\>*

</b></dt>
<dd>

The format of the converted date.



</dd>
</dl>



<a name="loioa546abe884f21015bc048c3994136804__DATEFORMAT_returns1"/>

## Result Set

VARCHAR



<a name="loioa546abe884f21015bc048c3994136804__DATEFORMAT_remarks1"/>

## Remarks

The *<datetime-expression\>* to convert must be a date, time, or timestamp data type, but can also be a `CHAR` or `VARCHAR` character string. If the date is a character string, data lake Relational Engine implicitly converts the character string to date, time, or timestamp data type, so an explicit cast, as in the example above, is unnecessary.

Any allowable date format can be used for *<string-expression\>*. Date format strings cannot contain any multibyte characters. Only single-byte characters are allowed in a date/time/datetime format string, even when the collation order of the database is a multibyte collation order like 932JPN.

If '*<?\>*' represents a multibyte character, then the following query fails:

```
SELECT DATEFORMAT ( start_date, 'yy?') FROM Employees;
```

Instead, move the multibyte character outside of the date format string using the concatenation operator:

```
SELECT DATEFORMAT (start_date, 'yy') + '?' FROM Employees;
```



<a name="loioa546abe884f21015bc048c3994136804__DATEFORMAT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa546abe884f21015bc048c3994136804__DATEFORMAT_examples1"/>

## Examples

-   The following statement returns string values like “Jan 01, 1989”:

    ```
    SELECT DATEFORMAT( start_date, 'Mmm dd, yyyy' ) from Employees;
    ```

-   The following statement returns the string “Feb 19, 1987”:

    ```
    SELECT DATEFORMAT( CAST ( '1987/02/19' AS DATE ), 'Mmm Dd, yyyy' ) FROM iq_dummy;
    ```


**Related Information**  


[DATEFORMAT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/d8071cc3053447a9bd6d90807082d61a.html "Returns a string representing a date expression in the specified format.") :arrow_upper_right:

