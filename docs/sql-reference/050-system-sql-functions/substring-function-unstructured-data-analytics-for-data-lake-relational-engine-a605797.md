<!-- loioa605797284f210158739abd33dbbc317 -->

# SUBSTRING Function \[Unstructured Data Analytics\] for Data Lake Relational Engine

The `SUBSTRING` function returns a variable-length character string of the `LONG VARCHAR` column or variable parameter. If any of the arguments are NULL, `SUBSTRING` returns NULL.



```
{ SUBSTRING |  SUBSTR } ( <long-varchar-column>, <start> [, <length> ] );
```



<a name="loioa605797284f210158739abd33dbbc317__iq_iquda_187"/>

## Parameters


<dl>
<dt><b>

*<long-varchar-column\>*

</b></dt>
<dd>

The name of a `LONG VARCHAR` column or variable.



</dd><dt><b>

*<start\>*

</b></dt>
<dd>

An integer expression indicating the start of the substring. A positive integer starts from the beginning of the string, with the first character at position 1. A negative integer specifies a substring starting from the end of the string, with the final character at position -1.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

An integer expression indicating the character length of the substring. A positive length specifies the number of characters to return, starting at the *<start\>* position. A negative length specifies the number of characters to return, ending at the *<start\>* position.



</dd>
</dl>



<a name="loioa605797284f210158739abd33dbbc317__iq_iquda_188"/>

## Remarks

`SUBSTRING` supports `LONG VARCHAR` variables of any size of data. Currently, a SQL variable can hold up to 2 GB - 1 in length. `SUBSTRING` does not support `LONG BINARY` variables or searching `LONG BINARY` columns.

When the `ansi_substring` database option is set to ON \(default\), negative values are invalid.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

