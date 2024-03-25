<!-- loioa6048c0184f21015a7979e3062fa41c5 -->

# CHAR\_LENGTH64 Function \[Unstructured Data Analytics\] for Data Lake Relational Engine

The `CHAR_LENGTH64` function returns an unsigned 64-bit value containing the character length of the `LONG VARCHAR` column or variable parameter, including the trailing blanks.



```
CHAR_LENGTH64( <long-varchar-object> );
```



<a name="loioa6048c0184f21015a7979e3062fa41c5__iq_iquda_172"/>

## Parameters


<dl>
<dt><b>

*<long-varchar-object\>*

</b></dt>
<dd>

The name of a LONG VARCHAR column in a table or a LONG VARCHAR variable.



</dd>
</dl>



<a name="loioa6048c0184f21015a7979e3062fa41c5__iq_iquda_173"/>

## Remarks

CHAR\_LENGTH64 supports LONG VARCHAR columns and LONG VARCHAR variables of any size of data. Currently, a SQL variable can hold up to 2 GB - 1 in length.

If the argument is NULL, CHAR\_LENGTH64 returns NULL.

**Related Information**  


[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_1_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

