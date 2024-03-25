<!-- loio64302f89b4d04a0fae9e59e8530f27fe -->

# LPAD Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Left-pads a string with spaces, or a specified pattern, to make a string of a specified number of characters in length.



```
LPAD ( <str>, <n> [, <pattern> ] );
```



<a name="loio64302f89b4d04a0fae9e59e8530f27fe__section_t1z_mvg_trb"/>

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

The length to which to pad *<str\>*. *<n\>* must be an integer.



</dd><dt><b>

*<pattern\>*

</b></dt>
<dd>

A string of characters to use for padding instead of spaces.



</dd>
</dl>



<a name="loio64302f89b4d04a0fae9e59e8530f27fe__section_m3n_nvg_trb"/>

## Remarks

Left-pads the end of *<str\>* with spaces to make a string of *<n\>* characters. If *<pattern\>* is specified, then *<str\>* is padded using sequences of the given characters until the required length is met.

If the length of *<str\>* is greater than *<n\>*, then no padding is performed and the resulting value is truncated from the right side to the length specified in *<n\>*.

LPAD returns an empty string value if *<n\>* is less than 1.



<a name="loio64302f89b4d04a0fae9e59e8530f27fe__section_slg_mqh_trb"/>

## Standards and Compatibility

-   Vendor extension.




<a name="loio64302f89b4d04a0fae9e59e8530f27fe__section_fbc_qvg_trb"/>

## Examples

-   The following example left-pads the start of string `end` with the pattern `12345` to make a string of `15` characters in length, and returns the value ***1234512345hello***:

    ```
    SELECT LPAD ('hello', 15, '12345') "left pad" FROM DUMMY;
    ```

-   In the following example, *<str\>* is longer than *<n\>*, so no padding is performed and the result is *<str\>* truncated to the length of *<n\>* \(that is, ***he***\):

    ```
    SELECT LPAD ('hello', 2, '12345') "left pad" FROM DUMMY;
    ```

-   By not specifying *<pattern\>*, this example left-pads the start of string `hello` with a single blank character \(that is, "***hello***"\):

    ```
    SELECT LPAD ('hello', 6) "left pad" FROM DUMMY;
    ```


**Related Information**  


[LPAD Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/7bf4b4293b56487bbabf9c2f3d01b364.html "Left-pads a string with spaces, or a specified pattern, to make a string of a specified number of characters in length.") :arrow_upper_right:

