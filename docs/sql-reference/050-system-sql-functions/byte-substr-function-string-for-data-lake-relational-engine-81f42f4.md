<!-- loio81f42f4e6ce21014ab50bd987169f496 -->

# BYTE\_SUBSTR Function \[String\] for Data Lake Relational Engine

Returns a substring of a string. The substring is determined using bytes, not characters.



```
BYTE_SUBSTR( <source_string> , <start_position> [ , <length> ] );
```



<a name="loio81f42f4e6ce21014ab50bd987169f496__BYTE_SUBSTR_parm1"/>

## Parameters


<dl>
<dt><b>

*<source\_string\>* 

</b></dt>
<dd>

The data from which the binary substring is taken.



</dd><dt><b>

*<start\_position\>* 

</b></dt>
<dd>

An integer expression indicating the start of the substring. A positive integer starts from the beginning of the data, with the first byte being position 1. A negative integer specifies a substring starting from the end of the data, the final byte being at position -1.



</dd><dt><b>

*<length\>* 

</b></dt>
<dd>

An integer expression indicating the length of the substring. A positive *<length\>* specifies the number of bytes to be taken *starting* at the start position. A negative *<length\>* returns at most *<length\>* bytes up to, and including, the starting position, from the left of the starting position.



</dd>
</dl>



<a name="loio81f42f4e6ce21014ab50bd987169f496__BYTE_SUBSTR_returns1"/>

## Result Set

BINARY or LONG BINARY, depending on the length of the result.



<a name="loio81f42f4e6ce21014ab50bd987169f496__BYTE_SUBSTR_remarks1"/>

## Remarks

Both *<start\_position\>* and *<length\>* can be either positive or negative. Use appropriate combinations of negative and positive numbers, to get a substring from either the beginning or end of the string. If *<length\>* is specified, the maximum length of the substring is ABS\(*<length\>*\).

If *<start\_position\>* is zero and length is non-negative, then a *<start\_position\>* value of 1 is used. If *<start\_position\>* is zero and *<length\>* is negative, then a start value of -1 is used.

The argument *<source\_string\>* can be any data type that can be converted to a binary data type, and is treated as a binary string.



## Example

The following statement returns the binary value `0x54657374`, which is the hexadecimal representation of `Test`:

```
SELECT BYTE_SUBSTR( 'Test Message', 1, 4 );
```

**Related Information**  


[BYTE_SUBSTR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/e7559cd08946434ba594a85bc232958e.html "Returns a substring of a string. The substring is determined using bytes, not characters.") :arrow_upper_right:

