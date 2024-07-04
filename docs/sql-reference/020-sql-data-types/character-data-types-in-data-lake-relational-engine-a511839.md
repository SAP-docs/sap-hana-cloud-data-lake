<!-- loioa511839b84f210159df2d5d78c6e891f -->

# Character Data Types in Data Lake Relational Engine

Use character data types for storing strings of letters, numbers, and symbols.




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

CLOB

</td>
<td valign="top">

Supports character large object \(CLOB\) data with a length ranging from zero \(0\) to 512 TB \(terabytes\).

The maximum length is equal to 4 GB multiplied by the database page size \(512 KB\).

</td>
</tr>
<tr>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

Stores character data of arbitrary length. The maximum size in bytes is 2 GB minus 1 \(2<sup>31</sup> - 1\) or 2 147 483 647.

Multibyte characters can be stored as LONG VARCHAR, but the length is in bytes, not characters.

VARCHAR has no blank padding added to the storage of these strings.

</td>
</tr>
<tr>
<td valign="top">

TEXT

</td>
<td valign="top">

Stores character data of arbitrary length. TEXT is a domain, implemented as a LONG VARCHAR.

</td>
</tr>
<tr>
<td valign="top">

VARCHAR

</td>
<td valign="top">

Stores arbitrary length character data.

```
VARCHAR [ ( <max-length> [ BYTE | CHAR | CHARACTER ] ) ]
```


<dl>
<dt><b>

*<max-length\>*

</b></dt>
<dd>

If CHAR or CHARACTER \(byte-length semantics\) is not specified as part of the length, then the length is in bytes and must be in the range of 1 to 32767\(32 KB – 1\). If BYTE is specified,*<max-length\>* must be specified. If only VARCHAR is specified, then *<max-length\>* is 1 with byte-length semantic.

If CHAR or CHARACTER \(character-length semantics\) is specified as part of the length, then the length is in characters, and *<max-length\>* must be specified, to a maximum of 5000.



</dd>
</dl>

VARCHAR has no blank padding added to the storage of these strings.

All index types, except DATE, TIME, and DATETIME/TIMESTAMP are supported for VARCHAR data to a maximum of to 255 bytes in length. For VARCHAR using character-length semantic, the maximum byte length depends on the number of bytes used per character. The limit becomes 255 divided by the number of bytes per character.

</td>
</tr>
</table>



<a name="loioa511839b84f210159df2d5d78c6e891f__char_data_type_section2"/>

## Storage Sizes

The storage size of character data, given column definition size, and input data size.


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

VARCHAR

</td>
<td valign="top" rowspan="1">

Width of \(32 K – 1\) bytes

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes

</td>
<td valign="top" rowspan="1">

\(32 K – 1\) bytes

</td>
</tr>
</table>



<a name="loioa511839b84f210159df2d5d78c6e891f__char_data_type_section3"/>

## Long Strings

Values up to 254 characters are stored as short strings, with a preceding length byte. Any values that are longer than 255 bytes are considered long strings. Characters after the 255th are stored separate from the row containing the long string value.

Several functions ignore the part of any string past the 255th character. They’re SOUNDEX, SIMILAR, and all of the date functions. Also, any arithmetic involving the conversion of a long string to a number works on only the first 255 characters. It would be unusual to run in to one of these limitations.

All other functions and all other operators work with the full length of long strings.

