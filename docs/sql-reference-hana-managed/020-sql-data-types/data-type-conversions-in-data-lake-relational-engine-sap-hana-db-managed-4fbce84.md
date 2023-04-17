<!-- loio4fbce848b988450d8fa96a7dc640fcbf -->

# Data Type Conversions in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Type conversions happen automatically, or you can explicitly request them using the CAST or CONVERT function.



If a string is used in a numeric expression or as an argument to a function expecting a numeric argument, then the string is converted to a number before use.

If a number is used in a string expression or as a string function argument, then the number is converted to a string before use.

All date constants are specified as strings. The string is automatically converted to a date before use.

There are certain cases where the automatic data type conversions are not appropriate:

-   '12/31/90' + 5 – tries to convert the string to a number
-   'a' \> 0 – tries to convert 'a' to a number

You can use the CAST or CONVERT function to force type conversions.

You can also use the following functions to force type conversions:

-   DATE\( expression \) – converts the expression into a date, and removes any hours, minutes, or seconds. Conversion errors might be reported.

-   DATETIME\( expression \) – converts the expression into a timestamp. Conversion errors might be reported.

-   STRING\( expression \) – similar to CAST\(value AS VARCHAR\), except that string\(NULL\) is the empty string \(''\), whereas CAST\(NULL AS VARCHAR\) is the NULL value.


> ### Note:  
> Data lake Relational Engine does not silently truncate the conversion result of numeric and date data types to VARCHAR. A conversion error is generated when the following data types are converted to a string that is longer than the column width:
> 
> -   TINYINT, SMALLINT, \[UNSIGNED\] \{ INT | INTEGER \}, \[ UNSIGNED \] BIGINT
> -   NUMERIC, DECIMAL
> -   FLOAT, DOUBLE, REAL
> -   DATE, DATETIME, SMALLDATETIME, TIME, TIMESTAMP
> 
> The CONVERSION\_ERROR option controls data lake Relational Engine behavior in cases of conversion error. If you set the CONVERSION\_ERROR option to:
> 
> -   OFF – then data lake Relational Engine inserts a NULL value when possible
> 
> -   ON – then data lake Relational Engine rolls back the insert and logs a conversion error

