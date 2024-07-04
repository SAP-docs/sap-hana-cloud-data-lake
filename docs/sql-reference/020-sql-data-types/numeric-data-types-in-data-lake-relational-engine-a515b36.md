<!-- loioa515b36684f21015883bb712de9c8b4c -->

# Numeric Data Types in Data Lake Relational Engine

Use numeric data types for storing numerical data.




<table>
<tr>
<th valign="top" rowspan="1">

Data Type

</th>
<th valign="top" rowspan="1">

Description

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

BIGINT

</td>
<td valign="top" rowspan="1">

A signed 64-bit integer, requiring 8 bytes of storage.

```
[ UNSIGNED ] BIGINT
```

You can specify integers as UNSIGNED. By default the data type is signed. Its range is between -9223372036854775808 and 9223372036854775807 \(signed\) or from 0 to 18446744073709551615 \(unsigned\).

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

DECIMAL

</td>
<td valign="top" rowspan="1">

A signed decimal number with *<precision\>* total digits and with *<scale\>* of the digits after the decimal point.

```
DECIMAL [ ( <precision> [ , <scale> ] ) ]
```

*<precision\>* can equal 1 to 126, inclusive, specifying the number of digits in the expression. *<scale\>* can equal 0 up to precision value, specifying the number of digits after the decimal point. The defaults are scale = 38 and precision = 126. Results are calculated based on the actual data type of the column to ensure accuracy, but you can set the maximum scale of the result returned to the application using the MAX\_CLIENT\_NUMERIC\_SCALE option.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

DOUBLE

</td>
<td valign="top" rowspan="1">

A signed double-precision floating-point number stored in 8 bytes. The range of absolute, nonzero values is between 2.2250738585072014e-308 and 1.797693134862315708e+308. Values held as DOUBLE are accurate to 15 significant digits, but might be subject to rounding errors beyond the 15th digit.

The DOUBLE data type is an approximate numeric data type; it is subject to rounding errors after arithmetic operations.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

FLOAT

</td>
<td valign="top" rowspan="1">

Stores a floating-point number, which can be single or double precision.

```
FLOAT [ ( <precision> ) ]
```

If *<precision\>* supplied, then the FLOAT data type is the same as the REAL or DOUBLE data type, depending on the value of the precision. The cutoff between REAL and DOUBLE is platform-dependent, and it is the number of bits used in the mantissa of single-precision floating point number on the platform. If not supplied, then the FLOAT data type is the same as the REAL data type.

When a column is created using the FLOAT data type, columns on all platforms are guaranteed to hold the values to at least the specified minimum precision. In contrast, REAL and DOUBLE do not guarantee a platform-independent minimum precision.

The FLOAT data type is an approximate numeric data type; it is subject to rounding errors after arithmetic operations.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

INT or INTEGER

</td>
<td valign="top" rowspan="1">

Stores integers that require 4 bytes of storage.

```
[ UNSIGNED ] INT[EGER]
```

A signed 32-bit integer with a range of values between -2147483648 and 2147483647 requiring 4 bytes of storage.

The INTEGER data type is an exact numeric data type; its accuracy is preserved after arithmetic operations.

You can specify integers as UNSIGNED; by default the data type is signed. The range of values for an unsigned integer is between 0 and 4294967295.

</td>
</tr>
<tr>
<td valign="top">

MONEY

</td>
<td valign="top">

Stores monetary data. MONEY is a domain, implemented as NUMERIC\(19,4\).

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

NUMERIC

</td>
<td valign="top" rowspan="1">

Same as DECIMAL.

```
NUMERIC [ ( <precision> [ , <scale> ] ) ]
```



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

REAL

</td>
<td valign="top" rowspan="1">

A signed single-precision floating-point number stored in 4 bytes. The range of absolute, nonzero values is 1.175494351e-38 to 3.402823466e+38. Values held as REAL are accurate to 6 significant digits, but might be subject to rounding errors beyond the sixth digit.

The REAL data type is an approximate numeric data type; it is subject to rounding errors after arithmetic operations.

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

SMALLINT

</td>
<td valign="top" rowspan="1">

A signed 16-bit integer with a range between -32768 and 32767, requiring 2 bytes of storage.

The SMALLINT data type is an exact numeric data type; its accuracy is preserved after arithmetic operations.

</td>
</tr>
<tr>
<td valign="top">

SMALLMONEY

</td>
<td valign="top">

Stores monetary data that is less than one million currency units. SMALLMONEY is a domain, implemented as NUMERIC\(10,4\).

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

TINYINT

</td>
<td valign="top" rowspan="1">

An unsigned 8-bit integer with a range between 0 and 255, requiring 1 byte of storage.

The TINYINT data type is an exact numeric data type; its accuracy is preserved after arithmetic operations.

</td>
</tr>
</table>



-   The INTEGER, NUMERIC, and DECIMAL data types are sometimes called exact numeric data types, in contrast to the approximate numeric data types FLOAT, DOUBLE, and REAL. Only exact numeric data is guaranteed to be accurate to the least significant digit specified after arithmetic operations.

-   Do not fetch TINYINT columns into Embedded SQL variables defined as CHAR or UNSIGNED CHAR, since the result is an attempt to convert the value of the column to a string and then assign the first byte to the variable in the program.

-   A period is the only decimal separator \(decimal point\); comma is not supported as a decimal separator.



<a name="loioa515b36684f21015883bb712de9c8b4c__numeric_data_type_section3"/>

## Indexes

-   The CMP and HNG index types don’t support the FLOAT, DOUBLE, and REAL data types, and the HG index type isn’t recommended.

-   The WD, DATE, TIME, and DTTM index types don’t support the numeric data types.


