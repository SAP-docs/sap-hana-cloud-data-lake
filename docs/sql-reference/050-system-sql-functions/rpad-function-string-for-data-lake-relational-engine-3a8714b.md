<!-- loio3a8714b7782a4730b091194c3b54aca0 -->

# RPAD Function \[String\] for Data Lake Relational Engine

Right-pads a string with spaces or a specified pattern to make a string that is a specified number of characters in length.



```
RPAD ( <str>, <n> [, <pattern> ] );
```



<a name="loio3a8714b7782a4730b091194c3b54aca0__RPAD_parm1"/>

## Parameters


<dl>
<dt><b>

*<str\>*

</b></dt>
<dd>

The string to be padded.



</dd><dt><b>

*<n\>*

</b></dt>
<dd>

The length to pad *<str\>*. *<n\>* must be an integer.



</dd><dt><b>

*<pattern\>*

</b></dt>
<dd>

A string of characters, rather than spaces, to use for padding.



</dd>
</dl>



<a name="loio3a8714b7782a4730b091194c3b54aca0__RPAD_desc1"/>

## Description

Right-pads the end of *<str\>* with spaces or characters to make a string of *<n\>* characters in length. If *<pattern\>* is specified, then *<str\>* is padded using sequences of the given characters until the required length is met.

If the length of *<str\>* is greater than *<n\>*, then no padding is performed and the resulting value is truncated from the right side to the length specified in *<n\>*.

RPAD returns an empty string value if *<n\>* is less than 1.



<a name="loio3a8714b7782a4730b091194c3b54aca0__RPAD_standards1"/>

## Standards and Compatibility


<dl>
<dt><b>

SQL/2008

</b></dt>
<dd>

Vendor extension.



</dd>
</dl>



<a name="loio3a8714b7782a4730b091194c3b54aca0__RPAD_examples1"/>

## Examples

-   The following example right-pads the end of string `hello` with the pattern `12345` to make a string of `15` characters in length and returns the value "***hello1234512345***":

    ```
    SELECT RPAD ('hello', 15, '12345') "right pad" FROM DUMMY;
    ```

-   In this example, *<str\>* is longer than *<n\>*, so no padding is performed; the result is *<str\>* truncated to the length of *<n\>* \(that is, "***he***"\):

    ```
    SELECT RPAD ('hello', 2, '12345') "right pad" FROM DUMMY;
    ```

-   By not specifying *<pattern\>*, this example right-pads the end of string `hello` with a single blank character \(that is, "***hello***"\):

    ```
    SELECT RPAD ('hello', 6) "right pad" FROM DUMMY;
    ```


**Related Information**  


[RPAD Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/6c4ea243716a46e789d87818e8be6df1.html "Right-pads a string with spaces or a specified pattern to make a string that is a specified number of characters in length.") :arrow_upper_right:

