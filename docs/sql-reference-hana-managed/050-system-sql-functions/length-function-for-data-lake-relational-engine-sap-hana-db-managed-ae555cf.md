<!-- loioae555cf86ee34fe887637dbcd64a33c3 -->

# LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the number of characters in the specified string.



```
LENGTH ( <string-expression> )
```



<a name="loioae555cf86ee34fe887637dbcd64a33c3__section_gf2_w1h_trb"/>

## Parameters

 *<string-expression\>*
 :   The string.

 

<a name="loioae555cf86ee34fe887637dbcd64a33c3__section_k5q_w1h_trb"/>

## Returns

INT



<a name="loioae555cf86ee34fe887637dbcd64a33c3__section_vn1_x1h_trb"/>

## Remarks

If the string contains multibyte characters, and the proper collation is being used, LENGTH returns the number of characters, not the number of bytes. If the string is of BINARY data type, the LENGTH function behaves as BYTE\_LENGTH.

The LENGTH function is the same as the CHAR\_LENGTH function.



<a name="loioae555cf86ee34fe887637dbcd64a33c3__section_dy4_x1h_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioae555cf86ee34fe887637dbcd64a33c3__section_gkb_y1h_trb"/>

## Example

The following statement returns the value 9:

```
SELECT LENGTH( 'chocolate' ) FROM iq_dummy
```

**Related Information**  


[CHAR\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](char-length-function-for-data-lake-relational-engine-sap-hana-db-managed-c440e3a.md "Returns the number of characters in a string.")

[LEN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](len-function-for-data-lake-relational-engine-sap-hana-db-managed-a895aab.md "Takes one argument as an input of type BINARY or STRING and returns the number of characters, as defined by the database's collation sequence, of a specified string expression, excluding trailing blanks.")

[LENGTH Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a55ea65684f21015a60794ef54777c14.html "Returns the number of characters in the specified string.") :arrow_upper_right:

