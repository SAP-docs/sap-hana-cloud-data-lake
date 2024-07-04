<!-- loioa895aabb25c84638b38c77cd78d7ad00 -->

# LEN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Takes one argument as an input of type BINARY or STRING and returns the number of characters, as defined by the database's collation sequence, of a specified string expression, excluding trailing blanks.



```
LEN ( <string_expr> );
```



<a name="loioa895aabb25c84638b38c77cd78d7ad00__section_urq_nch_trb"/>

## Parameters


<dl>
<dt><b>

*<string\_expr\>*

</b></dt>
<dd>

The string expression to be evaluated.



</dd>
</dl>



<a name="loioa895aabb25c84638b38c77cd78d7ad00__section_ckc_4ch_trb"/>

## Remarks

The result may differ from the string’s byte length for multi-byte character sets.

BINARY and VARBINARY are also allowed, in which case LEN\(\) returns the number of bytes of the input.

LEN is an alias of LENGTH function

This function is the equivalent of CHAR\_LENGTH \(*<string\_expression \>*\).



<a name="loioa895aabb25c84638b38c77cd78d7ad00__section_dxq_4ch_trb"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa895aabb25c84638b38c77cd78d7ad00__section_x4z_4ch_trb"/>

## Examples

The following example returns the value 3152:

```
SELECT LEN(Photo) FROM Products WHERE ID = 500;
```

**Related Information**  


[LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](length-function-for-data-lake-relational-engine-sap-hana-db-managed-ae555cf.md "Returns the number of characters in the specified string.")

[LEN Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a55e08c884f210159d0cec6bce940d82.html "Takes one argument as an input of type BINARY or STRING and returns the number of characters, as defined by the database's collation sequence, of a specified string expression, excluding trailing blanks.") :arrow_upper_right:

