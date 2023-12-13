<!-- loioa604206f84f2101583baba4af8324641 -->

# BYTE\_SUBSTR64 and BYTE\_SUBSTR Functions \[Unstructured Data Analytics\] for Data Lake Relational Engine

The `BYTE_SUBSTR64` and `BYTE_SUBSTR` functions return the byte substring of the large object column or variable parameter.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
BYTE_SUBSTR64( <large-object-column>, <start>, <length> );
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
BYTE_SUBSTR( <large-object-column>, <start>, <length> );
```



</dd>
</dl>



<a name="loioa604206f84f2101583baba4af8324641__iq_iquda_166"/>

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

An integer expression indicating the start of the substring. A positive integer starts from the beginning of the string, with the first byte at position 1. A negative integer specifies a substring starting from the end of the string, with the final byte at position -1.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

An integer expression indicating the length of the substring. A positive length specifies the number of bytes to return, starting at the *<start\>* position. A negative length specifies the number of bytes to return, ending at the *<start\>* position.



</dd>
</dl>



<a name="loioa604206f84f2101583baba4af8324641__iq_iquda_167"/>

## Remarks

Nested operations of the functions `BYTE_LENGTH64`, `BYTE_SUBSTR64`, and `BYTE_SUBSTR` do not support large object columns or variables.

The `BYTE_SUBSTR64` and `BYTE_SUBSTR` functions support both `LONG BINARY` and `LONG VARCHAR` columns and `LONG BINARY` and `LONG VARCHAR` variables of any size of data. Currently, a SQL variable can hold up to 2 GB - 1 in length.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

[BYTE\_LENGTH64 Function \[String\] for Data Lake Relational Engine](byte-length64-function-string-for-data-lake-relational-engine-a538947.md "BYTE_LENGTH64 returns an unsigned 64-bit value containing the byte length of the LONG BINARY column parameter.")

