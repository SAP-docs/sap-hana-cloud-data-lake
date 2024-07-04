<!-- loioa55548d184f21015b2d58684e0bb094a -->

# HEXTOBIGINT Function \[Data Type Conversion\] for Data Lake Relational Engine

Returns the BIGINT equivalent of a hexadecimal string.



```
HEXTOBIGINT ( <hexadecimal-string> );
```



<a name="loioa55548d184f21015b2d58684e0bb094a__HEXTOBIGINT_parm1"/>

## Parameters


<dl>
<dt><b>

*<hexadecimal-string\>*

</b></dt>
<dd>

The hexadecimal value to be converted to a big integer \(BIGINT\). Input can be in the following forms, with either a lowercase or uppercase “0x” in the prefix, or no prefix:

```
0x<hex-string>
```

```
0X<hex-string>
```

```
<hex-string>
```



</dd>
</dl>



<a name="loioa55548d184f21015b2d58684e0bb094a__HEXTOBIGINT_remarks1"/>

## Remarks

The HEXTOBIGINT function accepts hexadecimal integers and returns the BIGINT equivalent. Hexadecimal integers can be provided as CHAR and VARCHAR value expressions, as well as BINARY and VARBINARY expressions.

The HEXTOBIGINT function accepts a valid hexadecimal string, with or without a “0x” or “0X” prefix, enclosed in single quotes.

Input of fewer than 16 digits is assumed to be left-padded with zeros.

For data type conversion failure on input, an error is returned unless the CONVERSION\_ERROR option is set to OFF. When CONVERSION\_ERROR is OFF, invalid hexadecimal input returns NULL.

An error is returned if a BINARY or VARBINARY value exceeds 8 bytes and a CHAR or VARCHAR value exceeds 16 characters, with the exception of the value being appended with ‘0x.’



<a name="loioa55548d184f21015b2d58684e0bb094a__HEXTOBIGINT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa55548d184f21015b2d58684e0bb094a__HEXTOBIGINT_example1"/>

## Examples

The following statements return the value 4294967287:

```
SELECT HEXTOBIGINT ( '0xfffffff7' ) FROM iq_dummy;
```

```
SELECT HEXTOBIGINT ( '0Xfffffff7' ) FROM iq_dummy;
```

```
SELECT HEXTOBIGINT ( 'fffffff7' ) FROM iq_dummy;
```

**Related Information**  


[CONVERSION\_ERROR Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/conversion-error-option-tsql-for-data-lake-relational-engine-a63018a.md "Controls reporting of data type conversion failures on fetching information from the database.")

[HEXTOBIGINT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/afd4faa8d87d4e4c90a0159fb250d01d.html "Returns the BIGINT equivalent of a hexadecimal string.") :arrow_upper_right:

