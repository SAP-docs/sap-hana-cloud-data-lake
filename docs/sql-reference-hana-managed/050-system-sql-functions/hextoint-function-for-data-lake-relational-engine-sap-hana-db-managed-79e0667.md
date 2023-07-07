<!-- loio79e066782ff645e8b6014d4f4d1e0d9e -->

# HEXTOINT Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the unsigned BIGINT equivalent of a hexadecimal string.



```
HEXTOINT ( <hexadecimal-string> )
```



<a name="loio79e066782ff645e8b6014d4f4d1e0d9e__section_irj_fpg_trb"/>

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



<a name="loio79e066782ff645e8b6014d4f4d1e0d9e__section_l4x_fpg_trb"/>

## Returns

The HEXTOINT function returns the platform-independent SQL INTEGER equivalent of the hexadecimal string. The hexadecimal value represents a negative integer if the 8th digit from the right is one of the digits 8-9 and the uppercase or lowercase letters A-F and the previous leading digits are all uppercase or lowercase letter F. The following is not a valid use of HEXTOINT since the argument represents a positive integer value that cannot be represented as a signed 32-bit integer:

```
SELECT HEXTOINT( '0x0080000001' );
```

INT



<a name="loio79e066782ff645e8b6014d4f4d1e0d9e__section_lbw_gpg_trb"/>

## Remarks

For invalid hexadecimal input, data lake Relational Engine returns an error unless the CONVERSION\_ERROR option is OFF. When CONVERSION\_ERROR is OFF, invalid hexadecimal input returns NULL.

See [CONVERSION_ERROR Option [TSQL] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a63018a284f210159f458fb9eec74501.html "Controls reporting of data type conversion failures on fetching information from the database.") :arrow_upper_right:.



<a name="loio79e066782ff645e8b6014d4f4d1e0d9e__section_u1j_hpg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio79e066782ff645e8b6014d4f4d1e0d9e__section_qww_hpg_trb"/>

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


[HEXTOINT Function [Data Type Conversion] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a555d0f984f210158262871887ce5bc9.html "Returns the unsigned BIGINT equivalent of a hexadecimal string.") :arrow_upper_right:

