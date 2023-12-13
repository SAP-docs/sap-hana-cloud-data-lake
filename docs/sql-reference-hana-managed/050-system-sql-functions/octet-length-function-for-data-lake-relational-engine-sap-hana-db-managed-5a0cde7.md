<!-- loio5a0cde720c794a5e877759b652354e75 -->

# OCTET\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns an unsigned 64-bit value containing the byte length of the column parameter.



```
OCTET_LENGTH( <column-name> );
```



<a name="loio5a0cde720c794a5e877759b652354e75__section_qpq_3mn_vrb"/>

## Parameters


<dl>
<dt><b>

*<column-name\>*

</b></dt>
<dd>

The name of a column.



</dd>
</dl>



<a name="loio5a0cde720c794a5e877759b652354e75__section_vw1_jmn_vrb"/>

## Remarks

The return value of a NULL argument is NULL.

The `OCTET_LENGTH` function supports all data lake Relational Engine data types.

The `OCTET_LENGTH` function supports all data lake Relational Engine data types and `LONG VARCHAR` and `LONG BINARY` variables of any size of data. Currently, a SQL variable can hold up to 2 GB - 1 in length.



<a name="loio5a0cde720c794a5e877759b652354e75__section_crt_jmn_vrb"/>

## Standards and Compatibility

SAP database products – not supported by SAP Adaptive Server Enterprise or SAP SQL Anywhere

**Related Information**  


[OCTET_LENGTH Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a56c053484f21015952de04bc4dab521.html "Returns an unsigned 64-bit value containing the byte length of the column parameter.") :arrow_upper_right:

