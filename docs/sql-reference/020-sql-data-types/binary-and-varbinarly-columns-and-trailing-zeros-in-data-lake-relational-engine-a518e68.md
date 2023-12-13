<!-- loioa518e68e84f21015b0fbba8c42dc8534 -->

# BINARY and VARBINARLY Columns and Trailing Zeros in Data Lake Relational Engine

All BINARY columns are padded with zeros to the full width of the column. Trailing zeros are truncated in all VARBINARY columns.



The following example creates a table with all four variations of BINARY and VARBINARY data types defined with NULL and NOT NULL. The same data is inserted in all four columns and is padded or truncated according to the data type of the column:

```
CREATE TABLE zeros (bnot BINARY(5) NOT NULL,
            bnull BINARY(5) NULL,
            vbnot VARBINARY(5) NOT NULL,
            vbnull VARBINARY(5) NULL);
INSERT zeros VALUES (0x12345000, 0x12345000,
            0x12345000, 0x12345000);
INSERT zeros VALUES (0x123, 0x123, 0x123, 0x123);
INSERT zeros VALUES (0x0, 0x0, 0x0, 0x0);
INSERT zeros VALUES ('002710000000ae1b',
            '002710000000ae1b', '002710000000ae1b',
            '002710000000ae1b');
SELECT * FROM zeros;
```


<table>
<tr>
<th valign="top">

bnot

</th>
<th valign="top">

bnull

</th>
<th valign="top">

vbnot

</th>
<th valign="top">

vbnull

</th>
</tr>
<tr>
<td valign="top">

0x1234500000

</td>
<td valign="top">

0x1234500000

</td>
<td valign="top">

0x12345000

</td>
<td valign="top">

0x12345000

</td>
</tr>
<tr>
<td valign="top">

0x0123000000

</td>
<td valign="top">

0x0123000000

</td>
<td valign="top">

0x0123

</td>
<td valign="top">

0x0123

</td>
</tr>
<tr>
<td valign="top">

0x0000000000

</td>
<td valign="top">

0x0000000000

</td>
<td valign="top">

0x00

</td>
<td valign="top">

0x00

</td>
</tr>
<tr>
<td valign="top">

0x3030323731

</td>
<td valign="top">

0x3030323731

</td>
<td valign="top">

0x3030323731

</td>
<td valign="top">

0x3030323731

</td>
</tr>
</table>

Because each byte of storage holds two hexadecimal digits, data lake Relational Engine expects binary entries to consist of the characters "0x" followed by an even number of digits. When the "0x" is followed by an odd number of digits, data lake Relational Engine assumes that you omitted the leading 0 and adds it for you.

Input values "0x00" and "0x0" are stored as "0x00" in variable-length binary columns \(VARBINARY\). In fixed-length binary columns \(BINARY\), the value is padded with zeros to the full length of the field:

```
INSERT zeros VALUES (0x0, 0x0, 0x0, 0x0);
SELECT * FROM zeros 
```


<table>
<tr>
<th valign="top">

not

</th>
<th valign="top">

bnull

</th>
<th valign="top">

vbnot

</th>
<th valign="top">

vbnull

</th>
</tr>
<tr>
<td valign="top">

0x0000000000

</td>
<td valign="top">

0x0000000000

</td>
<td valign="top">

0x00

</td>
<td valign="top">

0x00

</td>
</tr>
</table>

If the input value does not include "0x", then data lake Relational Engine assumes that the value is an ASCII value and converts it. For example:

```
CREATE TABLE sample (col_bin BINARY(8));
INSERT sample VALUES ('002710000000ae1b');SELECT * FROM sample;
```


<table>
<tr>
<th valign="top">

col\_bin

</th>
</tr>
<tr>
<td valign="top">

0x3030323731303030

</td>
</tr>
</table>

> ### Note:  
> In the above example, ensure you set the string\_rtruncation option to "off".

When you select a BINARY value, specify the value with the padded zeros or use the CAST function, as shown in these examples:

```
SELECT * FROM zeros WHERE bnot = 0x0123000000;
```

```
SELECT * FROM zeros WHERE bnot = CAST(0x0123 as binary(5));
```

