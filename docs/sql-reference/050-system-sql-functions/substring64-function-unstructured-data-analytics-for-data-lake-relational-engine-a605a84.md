<!-- loioa605a84d84f21015b7b18df02e62f0c4 -->

# SUBSTRING64 Function \[Unstructured Data Analytics\] for Data Lake Relational Engine

The `SUBSTRING64` function returns a variable-length character string of the large object column or variable parameter.



```
SUBSTRING64 ( <large-object-column>, <start> [, <length> ] );
```



<a name="loioa605a84d84f21015b7b18df02e62f0c4__iq_iquda_190"/>

## Parameters


<dl>
<dt><b>

*<large-object-column\>*

</b></dt>
<dd>

The name of a `LONG VARCHAR` or `LONG BINARY` column or variable.



</dd><dt><b>

*<start\>*

</b></dt>
<dd>

An 8-byte integer indicating the start of the substring. `SUBSTRING64` interprets a negative or zero *<start\>* offset as if the string were padded on the left with "non-characters." The first character starts at position 1.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

An 8-byte integer indicating the length of the substring. If *<length\>* is negative, an error is returned.



</dd>
</dl>



<a name="loioa605a84d84f21015b7b18df02e62f0c4__iq_iquda_191"/>

## Example

Values returned by `SUBSTRING64`, given a column named `col1` that contains the string \("ABCDEFG"\):

-   `SUBSTRING64( col1, 2, 4 )` returns the string "BCDE"
-   `SUBSTRING64( col1, 1, 3 )` returns the string "ABC"
-   `SUBSTRING64( col1, 0, 3 )` returns the string "AB"
-   `SUBSTRING64( col1, -1, 3 )` returns the string "A"



<a name="loioa605a84d84f21015b7b18df02e62f0c4__iq_iquda_192"/>

## Remarks

-   If any of the arguments are NULL, `SUBSTRING64` returns NULL.
-   Nested operations of the functions `SUBSTRING64`, `SUBSTRING`, `SUBSTR`, `BYTE_SUBSTR`, and `BYTE_SUBSTR64` do not support large object columns or variables.
-   `SUBSTRING64` supports searching `LONG VARCHAR` and `LONG BINARY` columns and `LONG VARCHAR` and `LONG BINARY` variables of any size of data. Currently, a SQL variable can hold up to 2GB - 1 in length.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_1_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

