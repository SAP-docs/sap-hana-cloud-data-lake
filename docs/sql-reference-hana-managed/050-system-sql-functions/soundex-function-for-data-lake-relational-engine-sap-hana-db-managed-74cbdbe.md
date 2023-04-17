<!-- loio74cbdbe37b6244ce8ac19780a8962f9e -->

# SOUNDEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a number representing the sound of a string.



```
SOUNDEX ( <string-expression> )
```



<a name="loio74cbdbe37b6244ce8ac19780a8962f9e__section_iwh_qx5_vrb"/>

## Parameters

 *<string-expression\>*
 :   The string.

 

<a name="loio74cbdbe37b6244ce8ac19780a8962f9e__section_tkv_qx5_vrb"/>

## Returns

SMALLINT



<a name="loio74cbdbe37b6244ce8ac19780a8962f9e__section_gm2_rx5_vrb"/>

## Remarks

The `SOUNDEX` function value for a string is based on the first letter and the next three consonants other than H, Y, and W. Doubled letters are counted as one letter. The following example is based on the letters A, P, L, and S:

```
SOUNDEX( 'apples' ) FROM iq_dummy
```

Multibyte characters are ignored by the `SOUNDEX` function.

Although it is not perfect, `SOUNDEX` normally returns the same number for words that sound similar and that start with the same letter.



<a name="loio74cbdbe37b6244ce8ac19780a8962f9e__section_zcc_sx5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio74cbdbe37b6244ce8ac19780a8962f9e__section_i5n_sx5_vrb"/>

## Example

The following statement returns two numbers, representing the sound of each name. The `SOUNDEX` value for each argument is 3827:

```
SELECT SOUNDEX( 'Smith' ), SOUNDEX( 'Smythe' ) FROM iq_dummy
```

`SOUNDEX` \( 'Smith' \) is equal to `SOUNDEX` \( 'Smythe' \).

**Related Information**  


[SOUNDEX Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a580dde084f21015b422a82fcc67a159.html "Returns a number representing the sound of a string.") :arrow_upper_right:

