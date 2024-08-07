<!-- loioc50b5a76f7684960a88e942bd46d6221 -->

# Binary Data Types in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Use binary data types for storing raw binary data, such as pictures, in a hexadecimal-like notation.



You can specify the column length in bytes, or use the default length of 1 byte. Each byte stores two hexadecimal digits. Even though the default length is 1 byte, it is recommended that you always specify an even number of characters for BINARY and VARBINARY column length. If you enter a value longer than the specified column length, then data lake Relational Engine truncates the entry to the specified length without warning or error.

Binary data begins with the characters “0x” or “0X” and can include any combination of digits and the uppercase and lowercase letters A through F.


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

BINARY

</td>
<td valign="top">

Binary data of a specified maximum *<length\>* in bytes.

```
BINARY [ ( <length> ) ]
```

If *<length\>* is omitted, then the default is 1 byte. The maximum size allowed is 32,767 bytes.

Use the fixed-length binary type BINARY for data in which all entries are expected to be approximately equal in length. Because entries in BINARY columns are zero-padded to the column length *<length\>*, they might require more storage space than entries in VARBINARY columns.

Use the fixed-length binary type BINARY for data in which all entries are expected to be approximately equal in length. Because entries in BINARY columns are zero-padded to the column length *<length\>*, they could require more storage space than entries in VARBINARY columns.

-   You can’t use the aggregate functions SUM, AVG, STDDEV, or VARIANCE with binary data types. The aggregate functions MIN, MAX, and COUNT support the BINARY data type.

-   HNG, WD, DATE, TIME, and DTTM indexes don’t support BINARY data.

-   Only the default index, CMP index, and TEXT index types are supported for BINARY data greater than 255 bytes in length.

-   Bit operations are supported on BINARY data that is 8 bytes or less in length.


All BINARY columns are padded with zeros to the full width of the column. Trailing zeros are truncated in all VARBINARY columns.

</td>
</tr>
<tr>
<td valign="top">

BLOB

</td>
<td valign="top">

BLOB \(binary large object\) data is supported with a length ranging from zero \(0\) to 2 PB \(petabytes\). BLOB is an alias for LONG BINARY data type. The maximum length is equal to 4 GB multiplied by the database page size \(512 KB\).

</td>
</tr>
<tr>
<td valign="top">

IMAGE

</td>
<td valign="top">

Stores binary data of arbitrary length.

IMAGE is a domain, implemented as LONG BINARY.

You can’t use the aggregate functions SUM, AVG, STDDEV, or VARIANCE with binary data types.

</td>
</tr>
<tr>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

Stores binary data of arbitrary length.

The maximum length of a long binary column is 2 PB.

The maximum size in bytes is 2 GB minus 1 byte or 2147483647.

You can’t use the SUM, AVG, STDDEV, or VARIANCE aggregate functions with binary data types.

</td>
</tr>
<tr>
<td valign="top">

UNIQUEIDENTIFIER

</td>
<td valign="top">

Stores UUID \(also known as GUID\) values.

The UNIQUEIDENTIFIER data type is often used for a primary key or other unique column to hold UUID \(Universally Unique Identifier\) values that can be used to uniquely identify rows. The NEWID function generates UUID values in such a way that a value produced on one computer doesn’t match a UUID produced on another computer. UNIQUEIDENTIFIER values generated using NEWID can therefore be used as keys in a synchronization environment.

The STRTOUUID and UUIDTOSTR functions convert values between UNIQUEIDENTIFIER and string representations.

UNIQUEIDENTIFIER values are stored and returned as BINARY\(16\).

Because UNIQUEIDENTIFIER values are large, using UNSIGNED BIGINT or UNSIGNED INT identity columns instead of UNIQUEIDENTIFIER is more efficient when you don’t need cross-database unique identifiers.

You can’t use the aggregate functions SUM, AVG, STDDEV, or VARIANCE with the UNIQUIEIDENTIFIER data type.

The following statement updates the table MYTAB and sets the value of the column uid\_col to a unique identifier generated by the NEWID function, if the current value of the column is NULL:

```
UPDATE MYTAB
    SET uid_col = NEWID()
      WHERE uid_col IS NULL;
```

1.  If you execute the following statement, then the unique identifier is returned as a BINARY\(16\):

    ```
    SELECT NEWID();
    ```

2.  For example, the value could be 0xd3749fe09cf446e399913bc6434f1f08. You can convert this string into a readable format using the UUIDTOSTR function.




</td>
</tr>
<tr>
<td valign="top">

VARBINARY

</td>
<td valign="top">

Binary data up to a specified *<max-length\>* in bytes.

```
VARBINARY [ ( <length> ) ]
```

If *<length\>* is omitted, then the default is 1 byte. The maximum size allowed is \(32 K – 1\) bytes. Use the variable-length binary type VARBINARY for data that is expected to vary greatly in length.

Use the variable-length binary type VARBINARY for data that is expected to vary greatly in length.

-   You can’t use the aggregate functions SUM, AVG, STDDEV, or VARIANCE with binary data types. The aggregate functions MIN, MAX, and COUNT support the VARBINARY data type.

-   HNG, WD, DATE, TIME, and DTTM indexes don’t support VARBINARY data.

-   Only the default index, CMP index, and TEXT index types are supported for VARBINARY data greater than 255 bytes in length.

-   Bit operations are supported on VARBINARY data that is 8 bytes or less in length.


All BINARY columns are padded with zeros to the full width of the column. Trailing zeros are truncated in all VARBINARY columns.

</td>
</tr>
</table>



<a name="loioc50b5a76f7684960a88e942bd46d6221__section_pxr_ppw_rvb"/>

## String Operators

The concatenation string operators || and + both support binary type data.

Explicit conversion of binary operands to character data types isn’t necessary with the || operator. Explicit and implicit data conversion produces different results, however.



<a name="loioc50b5a76f7684960a88e942bd46d6221__section_vhz_qpw_rvb"/>

## Storage Size

The storage size of binary data differs based on data type.


<table>
<tr>
<th valign="top" rowspan="1">

Data Type

</th>
<th valign="top" rowspan="1">

Column Definition

</th>
<th valign="top" rowspan="1">

Input Data

</th>
<th valign="top" rowspan="1">

Storage

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

VARBINARY

</td>
<td valign="top" rowspan="1">

width of \(32 K – 1\) bytes

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes binary

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

VARBINARY

</td>
<td valign="top" rowspan="1">

width of \(32K– 1\) bytes

</td>
<td valign="top" rowspan="1">

\(64 K – 2\) bytes ASCII

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

BINARY

</td>
<td valign="top" rowspan="1">

width of \(32 K – 1\) bytes

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes binary

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

BINARY

</td>
<td valign="top" rowspan="1">

width of \(32 K – 1\) bytes

</td>
<td valign="top" rowspan="1">

\(64 K – 2\) bytes ASCII

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes

</td>
</tr>
</table>

The exact form in which you enter a particular value depends on the platform you’re using. Therefore, calculations involving binary data can produce different results on different machines.

The CONVERT function uses little-endian semantics in data lake Relational Engine. For big-endian semantics, use the INTTOHEX and HEXTOINT functions.

**Related Information**  


[Binary Data Types in Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a517b59284f2101595fc9d23db89a857.html "Use binary data types for storing raw binary data, such as pictures, in a hexadecimal-like notation.") :arrow_upper_right:

