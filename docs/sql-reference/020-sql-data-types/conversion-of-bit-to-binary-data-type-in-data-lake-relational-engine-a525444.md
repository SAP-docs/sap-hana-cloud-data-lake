<!-- loioa525444184f210158a1c8f7a5a3c6a9e -->

# Conversion of BIT to BINARY Data Type in Data Lake Relational Engine

Data lake Relational Engine supports BIT to BINARY and BIT to VARBINARY implicit and explicit conversion and is compatible with SAP Adaptive Server Enterprise support of these conversions.

Data lake Relational Engine implicitly converts BIT to BINARY and BIT to VARBINARY data types for comparison operators, arithmetic operations, and INSERT and UPDATE statements.

For BIT to BINARY conversion, bit value ‘b’ is copied to the first byte of the binary string and the rest of the bytes are filled with zeros. For example, BIT value 1 is converted to BINARY\(n\) string 0x0100...00 having 2<sup>n</sup> nibbles. BIT value 0 is converted to BINARY string 0x00...00.

For BIT to VARBINARY conversion, BIT value ‘b’ is copied to the first byte of the BINARY string and the remaining bytes are not used; that is, only 1 byte is used. For example, BIT value 1 is converted to VARBINARY\(n\) string 0x01 having two nibbles.

The result of both implicit and explicit conversions of BIT to BINARY and BIT to VARBINARY data types is the same. The following table contains examples of BIT to BINARY and VARBINARY conversions.


<table>
<tr>
<th valign="top" rowspan="1">

Conversion of BIT Value ‘1’ to

</th>
<th valign="top" rowspan="1">

Result

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

BINARY\(3\)

</td>
<td valign="top" rowspan="1">

0x010000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

VARBINARY\(3\)

</td>
<td valign="top" rowspan="1">

0x01

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

BINARY\(8\)

</td>
<td valign="top" rowspan="1">

0x0100000000000000

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

VARBINARY\(8\)

</td>
<td valign="top" rowspan="1">

0x01

</td>
</tr>
</table>

These examples illustrate both implicit and explicit conversion of BIT to BINARY and BIT to VARBINARY data types.

Given the following tables and data:

```
CREATE TABLE tbin(c1 BINARY(9))
CREATE TABLE tvarbin(c2 VARBINARY(9))
CREATE TABLE tbar(c2 BIT)

INSERT tbar VALUES(1)
INSERT tbar VALUES(0)
```

Implicit conversion of BIT to BINARY:

```
INSERT tbin SELECT c2 FROM tbar

c1
---
0x010000000000000000   (18 nibbles)
0x000000000000000000   (18 nibbles)
```

Implicit conversion of BIT to VARBINARY:

```
INSERT tvarbin SELECT c2 FROM tbar

c2
---
0x01
0x00
```

Explicit conversion of BIT to BINARY:

```
INSERT tbin SELECT CONVERT (BINARY(9), c2) FROM tbar

c1
---
0x010000000000000000   (18 nibbles)
0x000000000000000000   (18 nibbles)
```

Explicit conversion of BIT to VARBINARY:

```
INSERT tvarbin SELECT CONVERT(VARBINARY(9), c2) FROM tbar

c2
---
0x01
0x00
```

