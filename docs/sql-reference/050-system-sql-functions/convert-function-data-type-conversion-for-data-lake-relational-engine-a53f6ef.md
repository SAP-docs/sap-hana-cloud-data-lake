<!-- loioa53f6efb84f21015af0e8594ce5cd68e -->

# CONVERT Function \[Data Type Conversion\] for Data Lake Relational Engine

Returns an expression converted to a supplied data type.



```
CONVERT ( <data-type>, <expression> [ , <format-style> ] );
```



<a name="loioa53f6efb84f21015af0e8594ce5cd68e__CONVERT_parm1"/>

## Parameters


<dl>
<dt><b>

*<data-type\>*

</b></dt>
<dd>

The data type to convert the expression into. Set the data type explicitly, or specify the %TYPE attribute to set the data type to the data type of a column in a table or view, or to the data type of a variable.



</dd><dt><b>

*<expression\>*

</b></dt>
<dd>

The expression to be converted.



</dd><dt><b>

*<format-style\>*

</b></dt>
<dd>

For converting strings to date or time data types and vice versa, format-style is a style code number that describes the date format string to be used.

If no *<format-style\>* argument is provided, the database option settings are used.



</dd>
</dl>



<a name="loioa53f6efb84f21015af0e8594ce5cd68e__CONVERT_returns1"/>

## Result Set

The data type specified.



<a name="loioa53f6efb84f21015af0e8594ce5cd68e__CONVERT_remarks1"/>

## Remarks

The result data type of a CONVERT function is a LONG VARCHAR. If you use CONVERT in a SELECT INTO statement, you'll need to use CAST and set CONVERT to the correct data type and size.

The CONVERT format style code output is as follows:


<table>
<tr>
<th valign="top">

Without Century \(yy\)

</th>
<th valign="top">

With Century \(yyyy\)

</th>
<th valign="top">

Output

</th>
</tr>
<tr>
<td valign="top">

–

</td>
<td valign="top">

0 or 100

</td>
<td valign="top">

mmm dd yyyy hh:nnAM \(or PM\)

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

101

</td>
<td valign="top">

mm/dd/yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

102

</td>
<td valign="top">

\[yy\]yy.mm.dd

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

103

</td>
<td valign="top">

dd/mm/yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

104

</td>
<td valign="top">

dd.mm.yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

105

</td>
<td valign="top">

dd-mm-yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

106

</td>
<td valign="top">

dd mmm yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

7

</td>
<td valign="top">

107

</td>
<td valign="top">

mmm dd, yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

108

</td>
<td valign="top">

hh:nn:ss

</td>
</tr>
<tr>
<td valign="top">

–

</td>
<td valign="top">

9 or 109

</td>
<td valign="top">

mmm dd yyyy hh:nn:ss:sssAM \(or PM\)

</td>
</tr>
<tr>
<td valign="top">

10

</td>
<td valign="top">

110

</td>
<td valign="top">

mm-dd-yy\[yy\]

</td>
</tr>
<tr>
<td valign="top">

11

</td>
<td valign="top">

111

</td>
<td valign="top">

\[yy\]yy/mm/dd

</td>
</tr>
<tr>
<td valign="top">

12

</td>
<td valign="top">

112

</td>
<td valign="top">

\[yy\]yymmdd

</td>
</tr>
<tr>
<td valign="top">

–

</td>
<td valign="top">

13 or 113

</td>
<td valign="top">

dd mmm yyyy hh:nn:ss:sss \(24 hour clock, Europe default + milliseconds, 4-digit year\)

</td>
</tr>
<tr>
<td valign="top">

14

</td>
<td valign="top">

114

</td>
<td valign="top">

hh:nn:ss \(24 hour clock\)

</td>
</tr>
<tr>
<td valign="top">

–

</td>
<td valign="top">

20 or 120

</td>
<td valign="top">

yyyy-mm-dd hh:nn:ss \(24-hour clock, ODBC canonical, 4-digit year\)

</td>
</tr>
<tr>
<td valign="top">

–

</td>
<td valign="top">

21 or 121

</td>
<td valign="top">

yyyy-mm-dd hh:nn:ss.sss \(24 hour clock, ODBC canonical with milliseconds, 4-digit year\)

</td>
</tr>
<tr>
<td valign="top">

36

</td>
<td valign="top">

136

</td>
<td valign="top">

hh:nn:ss.ssssssAM \(or PM\)

</td>
</tr>
<tr>
<td valign="top">

37

</td>
<td valign="top">

137

</td>
<td valign="top">

hh:nn:ss.ssssss

</td>
</tr>
<tr>
<td valign="top">

38

</td>
<td valign="top">

138

</td>
<td valign="top">

mmm dd yy\[yy\] hh:nn:ss.ssssssAM \(or PM\)

</td>
</tr>
<tr>
<td valign="top">

39

</td>
<td valign="top">

139

</td>
<td valign="top">

mmm dd yy\[yy\] hh:nn:ss.ssssss

</td>
</tr>
<tr>
<td valign="top">

40

</td>
<td valign="top">

140

</td>
<td valign="top">

\[yy\]yy-mm-dd hh:nn:ss.ssssss

</td>
</tr>
<tr>
<td valign="top">

–

</td>
<td valign="top">

365

</td>
<td valign="top">

yyyyjjj \(as a string or integer, where jjj is the Julian day number from 1 to 366 within the year\)

</td>
</tr>
</table>

Abbreviations and values for date parts in the CONVERT format style table:


<table>
<tr>
<th valign="top">

Abbreviation

</th>
<th valign="top">

Date Part

</th>
<th valign="top">

Values

</th>
</tr>
<tr>
<td valign="top">

hh

</td>
<td valign="top">

hour

</td>
<td valign="top">

0 – 23

</td>
</tr>
<tr>
<td valign="top">

nn

</td>
<td valign="top">

minute

</td>
<td valign="top">

0 – 59

</td>
</tr>
<tr>
<td valign="top">

ss

</td>
<td valign="top">

second

</td>
<td valign="top">

0 – 59

</td>
</tr>
<tr>
<td valign="top">

sss

</td>
<td valign="top">

millisecond

</td>
<td valign="top">

0 – 999

</td>
</tr>
<tr>
<td valign="top">

ssssss

</td>
<td valign="top">

microsecond

</td>
<td valign="top">

0 – 999999

</td>
</tr>
<tr>
<td valign="top">

mmm

</td>
<td valign="top">

month

</td>
<td valign="top">

jan to dec

</td>
</tr>
<tr>
<td valign="top">

dd

</td>
<td valign="top">

day

</td>
<td valign="top">

1 – 31

</td>
</tr>
<tr>
<td valign="top">

yyyy

</td>
<td valign="top">

year

</td>
<td valign="top">

0001 – 9999

</td>
</tr>
<tr>
<td valign="top">

mm

</td>
<td valign="top">

month

</td>
<td valign="top">

1 – 12

</td>
</tr>
</table>



<a name="loioa53f6efb84f21015af0e8594ce5cd68e__CONVERT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa53f6efb84f21015af0e8594ce5cd68e__CONVERT_example1"/>

## Example

The following statements illustrate the use of format styles:

```
SELECT CONVERT( CHAR( 20 ), order_date, 104 )
FROM sales_order;
```


<table>
<tr>
<th valign="top">

order\_date

</th>
</tr>
<tr>
<td valign="top">

16.03.1993

</td>
</tr>
<tr>
<td valign="top">

20.03.1993

</td>
</tr>
<tr>
<td valign="top">

23.03.1993

</td>
</tr>
<tr>
<td valign="top">

25.03.1993

</td>
</tr>
<tr>
<td valign="top">

...

</td>
</tr>
</table>

```
SELECT CONVERT( CHAR( 20 ), order_date, 7 )
FROM sales_order;
```


<table>
<tr>
<th valign="top">

order\_date

</th>
</tr>
<tr>
<td valign="top">

mar 16, 93

</td>
</tr>
<tr>
<td valign="top">

mar 20, 93

</td>
</tr>
<tr>
<td valign="top">

mar 23, 93

</td>
</tr>
<tr>
<td valign="top">

mar 25, 93

</td>
</tr>
<tr>
<td valign="top">

...

</td>
</tr>
</table>

```
SELECT order_datetime, CONVERT(CHAR(30), order_datetime, 40)
order_datetime40,
CONVERT(CHAR(30), order_datetime, 140) order_datetime140
FROM sales_order;
```


<table>
<tr>
<th valign="top">

order\_datetime

</th>
<th valign="top">

order\_datetime40

</th>
<th valign="top">

order\_datetime140

</th>
</tr>
<tr>
<td valign="top">

03/05/2009 01:03.05.123456

</td>
<td valign="top">

09-03-05 01:03:05.123456

</td>
<td valign="top">

2009-03-05 01:03:05.123456

</td>
</tr>
<tr>
<td valign="top">

03/05/2009 13:05.07.654321

</td>
<td valign="top">

09-03-05 13:05:07.654321

</td>
<td valign="top">

2009-03-05 13:05:07.654321

</td>
</tr>
</table>

```
SELECT CONVERT(CHAR(50), DATETIME('2009-11-03 11:10:42.033189'), 136) FROM iq_dummy;
```

returns `11:10:42.033189AM`.

```
SELECT CONVERT(CHAR(50), NOW(), 137) FROM iq_dummy;
```

returns `14:54:48.794122`.

The following statements illustrate the use of the format style 365, which converts data of type DATE and DATETIME to and from either string or integer type data:

```
CREATE TABLE tab
   (date_col DATE, int_col INT, char7_col CHAR(7));
INSERT INTO tab (date_col, int_col, char7_col)
   VALUES ('Dec 17, 2004', 2004352, '2004352');
```

-   ```
SELECT CONVERT(VARCHAR(8), tab.date_col, 365) FROM tab;
```

    returns `'2004352'`.

-   ```
SELECT CONVERT(INT, tab.date_col, 365) from tab;
```

    returns `2004352`.

-   ```
SELECT CONVERT(DATE, tab.int_col, 365) FROM TAB;
```

    returns `2004-12-17`.

-   ```
SELECT CONVERT(DATE, tab.char7_col, 365) FROM tab;
```

    returns `2004-12-17`.


The following statement illustrates conversion to an integer, and returns the value 5:

```
SELECT CONVERT( integer, 5.2 ) FROM iq_dummy;
```

**Related Information**  


[CAST Function \[Data Type Conversion\] for Data Lake Relational Engine](cast-function-data-type-conversion-for-data-lake-relational-engine-a53996d.md "Returns the value of an expression converted to a supplied data type.")

[HOURS Function \[Date and Time\] for Data Lake Relational Engine](hours-function-date-and-time-for-data-lake-relational-engine-a556e14.md "Returns the number of hours since an arbitrary starting date and time, the number of whole hours between two specified times, or adds the specified integer-expression number of hours to a time.")

[MINUTES Function \[Date and Time\] for Data Lake Relational Engine](minutes-function-date-and-time-for-data-lake-relational-engine-a5648d4.md "Returns the number of minutes since an arbitrary date and time, the number of whole minutes between two specified times, or adds the specified integer-expression number of minutes to a time.")

[MONTHS Function \[Date and Time\] for Data Lake Relational Engine](months-function-date-and-time-for-data-lake-relational-engine-a566ced.md "Returns the number of months since an arbitrary starting date/time or the number of months between two specified date/times, or adds the specified integer-expression number of months to a date/time.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[SECOND Function \[Date and Time\] for Data Lake Relational Engine](second-function-date-and-time-for-data-lake-relational-engine-a57dc03.md "Returns a number from 0 to 59 corresponding to the second component of the given date/time value.")

[WEEKS Function \[Date and Time\] for Data Lake Relational Engine](weeks-function-date-and-time-for-data-lake-relational-engine-a590601.md "Returns the number of weeks since an arbitrary starting date/time, returns the number of weeks between two specified date/times, or adds the specified integer-expression number of weeks to a date/time.")

[YEAR Function \[Date and Time\] for Data Lake Relational Engine](year-function-date-and-time-for-data-lake-relational-engine-a591eb9.md "Returns a 4-digit number corresponding to the year of the given date/time.")

[YEARS Function \[Date and Time\] for Data Lake Relational Engine](years-function-date-and-time-for-data-lake-relational-engine-a5926bf.md "Returns a 4-digit number corresponding to the year of a given date/time, returns the number of years between two specified date/times, or adds the specified integer-expression number of years to a date/time.")

[CONVERT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/b92624d74b14466cb6f758da6ed87324.html "Returns an expression converted to a supplied data type.") :arrow_upper_right:

