<!-- loio6c4ea243716a46e789d87818e8be6df1 -->

# RPAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Right-pads a string with spaces or a specified pattern to make a string that is a specified number of characters in length.



```
RPAD ( <str>, <n> [, <pattern> ] )
```



<a name="loio6c4ea243716a46e789d87818e8be6df1__section_pk2_crt_vrb"/>

## Parameters

 *<str\>*
 :   The string to be padded.

  *<n\>*
 :   The length to pad *<str\>*. *<n\>* must be an integer.

  *<pattern\>*
 :   A string of characters, rather than spaces, to use for padding.

 

<a name="loio6c4ea243716a46e789d87818e8be6df1__section_g4t_crt_vrb"/>

## Description

Right-pads the end of *<str\>* with spaces or characters to make a string of *<n\>* characters in length. If *<pattern\>* is specified, then *<str\>* is padded using sequences of the given characters until the required length is met.

If the length of *<str\>* is greater than *<n\>*, then no padding is performed and the resulting value is truncated from the right side to the length specified in *<n\>*.

RPAD returns an empty string value if *<n\>* is less than 1.



<a name="loio6c4ea243716a46e789d87818e8be6df1__section_klv_2rt_vrb"/>

## Standards and Compatibility

 SQL/2008
 :   Vendor extension.

 

<a name="loio6c4ea243716a46e789d87818e8be6df1__section_pxm_drt_vrb"/>

## Examples

-   The following example right-pads the end of string ***hello*** with the pattern ***12345*** to make a string of ***15*** characters in length and returns the value "***hello1234512345***":

    ```
    SELECT RPAD ('hello', 15, '12345') "right pad" FROM DUMMY;
    ```

-   In this example, *<str\>* is longer than *<n\>*, so no padding is performed; the result is *<str\>* truncated to the length of *<n\>* \(that is, "***he***"\):

    ```
    SELECT RPAD ('hello', 2, '12345') "right pad" FROM DUMMY;
    ```

-   By not specifying *<pattern\>*, this example right-pads the end of string ***hello*** with a single blank character \(that is, "***hello***"\):

    ```
    SELECT RPAD ('hello', 6) "right pad" FROM DUMMY;
    ```


**Related Information**  


[RPAD Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3a8714b7782a4730b091194c3b54aca0.html "Right-pads a string with spaces or a specified pattern to make a string that is a specified number of characters in length.") :arrow_upper_right:

