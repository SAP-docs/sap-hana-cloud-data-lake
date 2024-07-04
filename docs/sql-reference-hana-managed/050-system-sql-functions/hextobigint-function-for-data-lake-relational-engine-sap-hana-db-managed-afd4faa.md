<!-- loioafd4faa8d87d4e4c90a0159fb250d01d -->

# HEXTOBIGINT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the BIGINT equivalent of a hexadecimal string.



```
HEXTOBIGINT ( <hexadecimal-string> );
```



<a name="loioafd4faa8d87d4e4c90a0159fb250d01d__section_m3q_rpg_trb"/>

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



<a name="loioafd4faa8d87d4e4c90a0159fb250d01d__section_r5c_spg_trb"/>

## Remarks

The HEXTOBIGINT function accepts hexadecimal integers and returns the BIGINT equivalent. Hexadecimal integers can be provided as CHAR and VARCHAR value expressions, as well as BINARY and VARBINARY expressions.

The HEXTOBIGINT function accepts a valid hexadecimal string, with or without a “0x” or “0X” prefix, enclosed in single quotes.

Input of fewer than 16 digits is assumed to be left-padded with zeros.

For data type conversion failure on input, an error is returned unless the CONVERSION\_ERROR option is set to OFF. When CONVERSION\_ERROR is OFF, invalid hexadecimal input returns NULL.

An error is returned if a BINARY or VARBINARY value exceeds 8 bytes and a CHAR or VARCHAR value exceeds 16 characters, with the exception of the value being appended with ‘0x.’



<a name="loioafd4faa8d87d4e4c90a0159fb250d01d__section_dhs_spg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioafd4faa8d87d4e4c90a0159fb250d01d__section_rq1_tpg_trb"/>

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


[HEXTOBIGINT Function \[Data Type Conversion\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a55548d184f21015b2d58684e0bb094a.html "Returns the BIGINT equivalent of a hexadecimal string.") :arrow_upper_right:

