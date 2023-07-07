<!-- loioa604ead684f21015bc198a53acd1843c -->

# LOCATE Function \[Unstructured Data Analytics\] for Data Lake Relational Engine

The LOCATE function returns a 64-bit signed integer containing the position of the specified string in the large object column or variable parameter. For CHAR and VARCHAR columns, LOCATE returns a 32-bit signed integer position.



```
LOCATE( <large-object-column>, <string-expression>
[, <numeric-expression> ] )
```



<a name="loioa604ead684f21015bc198a53acd1843c__iq_iquda_178"/>

## Parameters


<dl>
<dt><b>

*<large-object-column\>*

</b></dt>
<dd>

The name of the LONG VARCHAR or LONG BINARY column or variable to search.



</dd><dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string of up to 255 bytes, for which you are searching.



</dd><dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The character position or offset at which to begin the search in the string. The *<numeric-expression\>* is a 64-bit signed integer for LONG VARCHAR and LONG BINARY columns and is a 32-bit signed integer for CHAR, VARCHAR, and BINARY columns. The first character is position 1. If the starting offset is negative, LOCATE returns the last matching string offset, rather than the first. A negative offset indicates how much of the end of the string to exclude from the search. The number of characters excluded is calculated as \( -1 \* offset \) - 1.



</dd>
</dl>



<a name="loioa604ead684f21015bc198a53acd1843c__iq_iquda_179"/>

## Remarks

-   All the positions or offsets, returned or specified, in the LOCATE function are always character offsets and may be different from the byte offset for multibyte data.
-   If the large object cell being searched contains more than one instance of the string:
    -   If *<numeric-expression\>* is specified, LOCATE starts the search at that offset in the string.
    -   If *<numeric-expression\>* is not specified, LOCATE returns only the position of the first instance.

-   If the column does not contain the string, LOCATE returns zero \(0\).
-   Searching for a string longer than 255 bytes returns NULL.
-   Searching for a zero-length string returns 1.
-   If any of the arguments is NULL, the result is NULL.
-   LOCATE supports searching LONG VARCHAR and LONG BINARY columns and LONG VARCHAR and LONG BINARY variables of any size of data. Currently, a SQL variable can hold up to 2 GB - 1 in length.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_2_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

