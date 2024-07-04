<!-- loioa605493584f21015acbba296e763a2eb -->

# PATINDEX Function \[Unstructured Data Analytics\] for Data Lake Relational Engine

The `PATINDEX` function returns a 64-bit unsigned integer containing the position of the first occurrence of the specified pattern in a `LONG VARCHAR` column or variable. For `CHAR` and `VARCHAR` columns, `PATINDEX` returns a 32-bit unsigned integer position.



```
PATINDEX( '<%pattern%>', <long-varchar-column> );
```



<a name="loioa605493584f21015acbba296e763a2eb__iq_iquda_184"/>

## Parameters


<dl>
<dt><b>

*<%pattern%\>*

</b></dt>
<dd>

The pattern for which you are searching. This string is limited to 126 bytes for patterns with wildcards. If you omit the leading percent wildcard, `PATINDEX` returns one \(1\) if the pattern occurs at the beginning of the column value, and zero \(0\) if the pattern does not occur at the beginning of the column value. Similarly, if you omit the trailing percent wildcard, the pattern should occur at the end of the column value. The pattern uses the same wildcards as the `LIKE` comparison.

Patterns without wildcards — percent \(%\) and underscore \(\_\) — can be up to 255 bytes in length.



</dd><dt><b>

*<long-varchar-column\>*

</b></dt>
<dd>

The name of the `LONG VARCHAR` column or variable.



</dd>
</dl>



<a name="loioa605493584f21015acbba296e763a2eb__iq_iquda_185"/>

## Remarks

-   All the positions or offsets, returned or specified, in the `PATINDEX` function are always character offsets and may be different from the byte offset for multibyte data.
-   If the `LONG VARCHAR` cell being searched contains more than one instance of the string pattern, `PATINDEX` returns only the position of the first instance.
-   If the column does not contain the pattern, `PATINDEX` returns zero \(0\).
-   Searching for a pattern longer than 126 bytes returns NULL.
-   Searching for a zero-length pattern returns 1.
-   If any of the arguments is NULL, the result is zero \(0\).
-   `PATINDEX` supports `LONG VARCHAR` variables of any size of data. Currently, a SQL variable can hold up to 2GB - 1 in length. `PATINDEX` does not support `LONG BINARY` variables or searching `LONG BINARY` columns.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_3_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

