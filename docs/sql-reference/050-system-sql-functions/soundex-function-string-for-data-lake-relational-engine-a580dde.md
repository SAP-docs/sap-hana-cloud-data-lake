<!-- loioa580dde084f21015b422a82fcc67a159 -->

# SOUNDEX Function \[String\] for Data Lake Relational Engine

Returns a number representing the sound of a string.



```
SOUNDEX ( <string-expression> );
```



<a name="loioa580dde084f21015b422a82fcc67a159__SOUNDEX_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string.



</dd>
</dl>



<a name="loioa580dde084f21015b422a82fcc67a159__SOUNDEX_returns1"/>

## Result Set

SMALLINT



<a name="loioa580dde084f21015b422a82fcc67a159__SOUNDEX_remarks1"/>

## Remarks

The `SOUNDEX` function value for a string is based on the first letter and the next three consonants other than H, Y, and W. Doubled letters are counted as one letter. The following example is based on the letters A, P, L, and S:

```
SOUNDEX( 'apples' ) FROM iq_dummy;
```

Multibyte characters are ignored by the `SOUNDEX` function.

Although it is not perfect, `SOUNDEX` normally returns the same number for words that sound similar and that start with the same letter.



<a name="loioa580dde084f21015b422a82fcc67a159__SOUNDEX_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa580dde084f21015b422a82fcc67a159__SOUNDEX_example1"/>

## Example

The following statement returns two numbers, representing the sound of each name. The `SOUNDEX` value for each argument is 3827:

```
SELECT SOUNDEX( 'Smith' ), SOUNDEX( 'Smythe' ) FROM iq_dummy;
```

`SOUNDEX` \( 'Smith' \) is equal to `SOUNDEX` \( 'Smythe' \).

**Related Information**  


[DIFFERENCE Function \[String\] for Data Lake Relational Engine](difference-function-string-for-data-lake-relational-engine-a54d8aa.md "Compares two strings, evaluates the similarity between them, and returns a value from 0 to 4.")

[SOUNDEX Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/74cbdbe37b6244ce8ac19780a8962f9e.html "Returns a number representing the sound of a string.") :arrow_upper_right:

