<!-- loioa555d0f984f210158262871887ce5bc9 -->

# HEXTOINT Function \[Data Type Conversion\] for Data Lake Relational Engine

Returns the unsigned BIGINT equivalent of a hexadecimal string.



```
HEXTOINT ( <hexadecimal-string> )
```



<a name="loioa555d0f984f210158262871887ce5bc9__HEXTOINT_parm1"/>

## Parameters


<dl>
<dt><b>

*<hexadecimal-string\>*

</b></dt>
<dd>

The string to be converted to an integer. Input can be in the following forms, with either a lowercase or uppercase “x” in the prefix, or no prefix:

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



<a name="loioa555d0f984f210158262871887ce5bc9__HEXTOINT_returns1"/>

## Returns

The HEXTOINT function returns the platform-independent SQL INTEGER equivalent of the hexadecimal string. The hexadecimal value represents a negative integer if the 8th digit from the right is one of the digits 8-9 and the uppercase or lowercase letters A-F and the previous leading digits are all uppercase or lowercase letter F. The following is not a valid use of HEXTOINT since the argument represents a positive integer value that cannot be represented as a signed 32-bit integer:

```
SELECT HEXTOINT( '0x0080000001' );
```

INT



<a name="loioa555d0f984f210158262871887ce5bc9__HEXTOINT_remarks1"/>

## Remarks

For invalid hexadecimal input, data lake Relational Engine returns an error unless the CONVERSION\_ERROR option is OFF. When CONVERSION\_ERROR is OFF, invalid hexadecimal input returns NULL.

See [CONVERSION\_ERROR Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/conversion-error-option-tsql-for-data-lake-relational-engine-a63018a.md).



<a name="loioa555d0f984f210158262871887ce5bc9__HEXTOINT_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa555d0f984f210158262871887ce5bc9__HEXTOINT_example1"/>

## Example

The following statements return the value 420:

```
SELECT HEXTOINT ( '0x1A4' ) FROM iq_dummy
```

```
SELECT HEXTOINT ( '0X1A4' ) FROM iq_dummy
```

```
SELECT HEXTOINT ( '1A4' ) FROM iq_dummy
```

**Related Information**  


[CONVERSION\_ERROR Option \[TSQL\] for Data Lake Relational Engine](../090-database-options/conversion-error-option-tsql-for-data-lake-relational-engine-a63018a.md "Controls reporting of data type conversion failures on fetching information from the database.")

[HEXTOINT Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/79e066782ff645e8b6014d4f4d1e0d9e.html "Returns the unsigned BIGINT equivalent of a hexadecimal string.") :arrow_upper_right:

