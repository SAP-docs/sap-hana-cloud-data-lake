<!-- loioa5370dd584f21015a902e1868e059b79 -->

# BIGINTTOHEX Function \[Data Type Conversion\] for Data Lake Relational Engine

Returns the hexadecimal equivalent in `VARCHAR(16)` of a decimal integer.



```
BIGINTTOHEX ( <integer-expression> );
```



<a name="loioa5370dd584f21015a902e1868e059b79__iq_refbb_256"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The integer to be converted to hexadecimal.



</dd>
</dl>



<a name="loioa5370dd584f21015a902e1868e059b79__iq_refbb_259"/>

## Remarks

`BIGINTTOHEX` accepts an integer expression that evaluates to `BIGINT` and returns the hexadecimal equivalent. Returned values are left appended with zeros up to a maximum of 16 digits. All types of unscaled integer data types are accepted as integer expressions.

Conversion is done automatically, if required. Constants are truncated, only if the fraction values are zero. A column cannot be truncated, if the column is declared with a positive scale value. If conversion fails, data lake Relational Engine returns an error unless the `CONVERSION_ERROR` option is `OFF`. In that case, the result is `NULL`.



<a name="loioa5370dd584f21015a902e1868e059b79__iq_refbb_260"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa5370dd584f21015a902e1868e059b79__iq_refbb_258"/>

## Examples

-   Returns the value `0000000000000009`:

    ```
    SELECT BIGINTTOHEX(9) FROM iq_dummy;
    ```

-   Returns the value `FFFFFFFFFFFFFFF7`:

    ```
    SELECT BIGINTTOHEX (-9) FROM iq_dummy;
    ```


