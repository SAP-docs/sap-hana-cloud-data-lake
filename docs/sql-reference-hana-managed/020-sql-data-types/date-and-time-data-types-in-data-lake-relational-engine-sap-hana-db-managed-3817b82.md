<!-- loio3817b82971be46b7a6b514a5ac93af34 -->

# Date and Time Data Types in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Use date and time data types for storing dates and times.




<table>
<tr>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

DATE



</td>
<td valign="top">

A calendar date, such as a year, month, and day. The year can be from 0001 to 9999. The day must be a nonzero value, so that the minimum date is 0001-01-01. A DATE value requires 4 bytes of storage.



</td>
</tr>
<tr>
<td valign="top">

DATETIME



</td>
<td valign="top">

A domain, implemented as TIMESTAMP. The fraction is stored to 6 decimal places \(not 7\). A DATETIME value requires 8 bytes of storage.



</td>
</tr>
<tr>
<td valign="top">

DATETIMEX



</td>
<td valign="top">

Point in time, containing year, month, day, hour, minute, second, and fraction of a second. The fraction is stored to 7 decimal places, regardless of the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option. The day must be a nonzero value. A DATETIMEX value requires 8 bytes of storage.



</td>
</tr>
<tr>
<td valign="top">

SMALLDATETIME



</td>
<td valign="top">

A domain, implemented as TIMESTAMP. A SMALLDATETIME value requires 8 bytes of storage.



</td>
</tr>
<tr>
<td valign="top">

TIME



</td>
<td valign="top">

Time of day, containing hour, minute, second, and fraction of a second. The fraction is stored to 6 decimal places. A TIME value requires 8 bytes of storage. \(ODBC standards restrict TIME data type to an accuracy of seconds. For this reason, do not use TIME data types in WHERE clause comparisons that rely on a higher accuracy than seconds.\)



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Point in time, containing year, month, day, hour, minute, second, and fraction of a second. The fraction is stored to 6 or 7 decimal precision, depending on the value of the TIMESTAMP\_COLUMNS\_AS\_DATETIMEX database option. For more information, see [Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine \(SAP HANA DB-Managed\)](decimal-precision-of-the-timestamp-data-type-in-data-lake-relational-engine-sap-hana-db-m-5cbca14.md). The day must be a nonzero value. A TIMESTAMP value requires 8 bytes of storage.



</td>
</tr>
</table>

The valid range of the TIMESTAMP data type is from 0001-01-01 00:00:00.000000 to 9999-12-31 23:59:59.999999. The display of TIMESTAMP data outside the range of 1600-02-28 23:59:59 to 7911-01-01 00:00:00 might be incomplete, but the complete datetime value is stored in the database; you can see the complete value by first converting it to a character string. You can use the CAST\(\) function to do this, as in the following example, which first creates a table with DATETIME and TIMESTAMP columns, then inserts values where the date is greater 7911-01-01:

```
create table mydates (id int, descript char(20),
  datetime_null datetime, timestamp_null timestamp);
```

```
insert into mydates values (1, 'example', '7911-12-30
  23:59:59','7911-12-30 06:03:44');
commit;
```

When you select without using CAST, hours and minutes are set to 00:00:

```
select * from mydates;
```

```
1, 'example', '7911-12-30 00:00:59.000', '7911-12-30 00:00:44.000'
```

When you select using cast, you see the complete timestamp:

```
select id, descript, cast(datetime_null as char(23)),
  cast(timestamp_null as char(23)) from mydates;
```

```
1, 'example', '7911-12-30 23:59:59.0', '7911-12-30 06:03:44.0'
```



<a name="loio3817b82971be46b7a6b514a5ac93af34__section_gkj_p4k_nvb"/>

## Index Types Supported

Date and time data support the following index types:

-   All date and time data types support the CMP, HG, and HNG index types; the WD index type isn’t supported.
-   DATE data supports the DATE index.
-   TIME data supports the TIME index.
-   DATETIME and TIMESTAMP data support the DTTM index.



<a name="loio3817b82971be46b7a6b514a5ac93af34__section_shh_s4k_nvb"/>

## Date and Time Comparisons

To compare a date to a string as a string, use the DATEFORMAT function or CAST function to convert the date to a string before comparing.

```
DATEFORMAT(invoice_date,'yyyy/mm/dd') = '1992/05/23'
```

You can use any allowable date format for the DATEFORMAT string expression.

Date format strings must not contain any multibyte characters. Only single-byte characters are allowed in a date/time/datetime format string, even when the collation order of the database is a multibyte collation order like 932JPN.

If '*<?\>*' represents a multibyte character, the following query fails:

```
SELECT DATEFORMAT ( StartDate, 'yy?') FROM Employees;
```

Instead, move the multibyte character outside of the date format string using the concatenation operator:

```
SELECT DATEFORMAT (StartDate, 'yy') + '?' FROM Employees;
```



<a name="loio3817b82971be46b7a6b514a5ac93af34__section_p4h_4sw_rvb"/>

## Unambiguous Dates and Times

Using the unambiguous date format prevents misinterpretation of dates according to the user's DATE\_ORDER setting.

Dates in the format *<yyyy\>*/*<mm\>*/*<dd\>* or *<yyyy\>*-*<mm\>*-*<dd\>* are always recognized as dates regardless of the DATE\_ORDER setting. You can use other characters as separators; for example, a question mark, a space character, or a comma. Use this format in any context where different users could be employing different DATE\_ORDER settings. For example, in stored procedures, use of the unambiguous date format prevents misinterpretation of dates according to the user's DATE\_ORDER setting.

A string of the form *<hh\>*:*<mm\>*:*<ss\>*.*<sss\>* is also interpreted unambiguously as a time.

For combinations of dates and times, any unambiguous date and any unambiguous time yield an unambiguous date-time value. Also, the following form is an unambiguous date-time value:

```
YYYY-MM-DD HH.MM.SS.SSSSSS
```

You can use periods in the time only in combination with a date.

In other contexts, you can use a more flexible date format. Data lake Relational Engine can interpret a wide range of strings as formats. The interpretation depends on the setting of the DATE\_ORDER database option. The DATE\_ORDER database option can have the value 'MDY', 'YMD', or 'DMY'. For example, to set the DATE\_ORDER option to 'DMY' enter:

```
SET OPTION DATE_ORDER = 'DMY' ;
```

The default DATE\_ORDER setting is 'YMD'. The ODBC driver sets the DATE\_ORDER option to 'YMD' whenever a connection is made. Use the SET OPTION statement to change the value.

The DATE\_ORDER database option determines whether the string 10/11/12 is interpreted by the database as Oct 11 1912, Nov 12 1910, or Nov 10 1912. The year, month, and day of a date string should be separated by some character \(for example "/", "-", or space\) and appear in the order specified by the DATE\_ORDER option.

You can supply the year as either two or four digits.

The month can be the name or number of the month.

The hours and minutes are separated by a colon, but can appear anywhere in the string.

It’s recommended that you specify the year using the four-digit format.

With an appropriate setting of DATE\_ORDER, the following strings are all valid dates:

```
99-05-23 21:35
99/5/23
1999/05/23
May 23 1999
23-May-1999
Tuesday May 23, 1999 10:00pm
```

If a string contains only a partial date specification, default values are used to fill out the date. The following defaults are used:

-   Year – 1900
-   Month – 1
-   Day – 1 \(useful for month fields; for example, 'May 1999' is the date '1999-05-01 00:00'\)
-   Hour, minute, second, fraction – 0

**Related Information**  


[Collations in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/665704355a5147879224d7ec0aae629f.html "Data lake Relational Engine databases use CESU8BIN (CESU-8, 8-bit multibyte encoding for Unicode, binary ordering) collation and the Unicode Collation Algorithm (UCA).") :arrow_upper_right:

[TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/timestamp-special-value-in-data-lake-relational-engine-sap-hana-db-managed-007a831.md "Returns when each row in the table was last modified.")

[CURRENT TIMESTAMP Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/current-timestamp-special-value-in-data-lake-relational-engine-sap-hana-db-managed-4bbfdd6.md "Combines CURRENT DATE and CURRENT TIME to form a TIMESTAMP value containing the year, month, day, hour, minute, second, and fraction of a second.")

[CURRENT TIME Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/current-time-special-value-in-data-lake-relational-engine-sap-hana-db-managed-098e867.md "Returns the current hour, minute, second, and fraction of a second.")

[CURRENT DATE Special Value in Data Lake Relational Engine \(SAP HANA DB-Managed\)](../010-sql-language-elements/current-date-special-value-in-data-lake-relational-engine-sap-hana-db-managed-3780258.md "Returns the current year, month, and day.")

[Retrieve Dates and Times in Data Lake Relational Engine \(SAP HANA DB-Managed\)](retrieve-dates-and-times-in-data-lake-relational-engine-sap-hana-db-managed-fabeab6.md "There are three ways in which you can retrieve dates and times from the database.")

[Decimal Precision of the TIMESTAMP Data Type in Data Lake Relational Engine \(SAP HANA DB-Managed\)](decimal-precision-of-the-timestamp-data-type-in-data-lake-relational-engine-sap-hana-db-m-5cbca14.md "Decimal precision for TIMESTAMP data type columns is controlled by the TIMESTAMP_COLUMNS_AS_DATETIMEX database option.")

[TIMESTAMP\_COLUMNS\_AS\_DATETIMEX Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../040-database-options/timestamp-columns-as-datetimex-option-for-data-lake-relational-engine-sap-hana-db-managed-34e3540.md "Controls whether DATETIMEX data type columns are automatically created when TIMESTAMPS data type columns are requested.")

