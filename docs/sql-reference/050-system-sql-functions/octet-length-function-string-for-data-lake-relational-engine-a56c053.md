<!-- loioa56c053484f21015952de04bc4dab521 -->

# OCTET\_LENGTH Function \[String\] for Data Lake Relational Engine

Returns an unsigned 64-bit value containing the byte length of the column parameter.



```
OCTET_LENGTH( <column-name> );
```



<a name="loioa56c053484f21015952de04bc4dab521__OCTET_LENGTH_parm1"/>

## Parameters


<dl>
<dt><b>

*<column-name\>*

</b></dt>
<dd>

The name of a column.



</dd>
</dl>



<a name="loioa56c053484f21015952de04bc4dab521__OCTET_LENGTH_remarks1"/>

## Remarks

The return value of a NULL argument is NULL.

The `OCTET_LENGTH` function supports all data lake Relational Engine data types.

The `OCTET_LENGTH` function supports all data lake Relational Engine data types and `LONG VARCHAR` and `LONG BINARY` variables of any size of data. Currently, a SQL variable can hold up to 2 GB - 1 in length.



<a name="loioa56c053484f21015952de04bc4dab521__OCTET_LENGTH_standards1"/>

## Standards and Compatibility

SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere

**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[Function Support of Large Object Data](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_4_QRC/en-US/a60363a384f21015a7f7bc6286516522.html "Learn about the functions that support the LONG BINARY and LONG VARCHAR data types.") :arrow_upper_right:

[OCTET_LENGTH Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/5a0cde720c794a5e877759b652354e75.html "Returns an unsigned 64-bit value containing the byte length of the column parameter.") :arrow_upper_right:

