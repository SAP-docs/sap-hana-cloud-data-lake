<!-- loio7d6e331baa6d4f8c90ff55b51d4bbb8e -->

# BIT\_LENGTH Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns an unsigned 64-bit value containing the bit length of the column parameter.



```
BIT_LENGTH( <column-name> );
```



<a name="loio7d6e331baa6d4f8c90ff55b51d4bbb8e__section_uhj_tgl_srb"/>

## Parameters


<dl>
<dt><b>

*<column-name\>*

</b></dt>
<dd>

The name of a column



</dd>
</dl>



<a name="loio7d6e331baa6d4f8c90ff55b51d4bbb8e__section_n5w_tgl_srb"/>

## Result Set

INT



<a name="loio7d6e331baa6d4f8c90ff55b51d4bbb8e__section_oq1_fll_srb"/>

## Remarks

The return value of a NULL argument is NULL.

The `BIT_LENGTH` function supports all data lake Relational Engine data types.



### Unstructured Data Analytics

`BIT_LENGTH` returns an unsigned 64-bit value containing the bit length of the large object column or variable parameter. Use the following syntax, where *<large-object-column\>* is the name of a `LONG VARCHAR` or `LONG BINARY` column or variable:

```
BIT_LENGTH( <large-object-column> );
```

The `BIT_LENGTH` function supports all data lake Relational Engine data types and `LONG BINARY` and `LONG VARCHAR` variables of any size of data, and returns an unsigned 64-bit value containing the bit length of the large object column or variable parameter.



<a name="loio7d6e331baa6d4f8c90ff55b51d4bbb8e__section_ipv_5gl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[BIT_LENGTH Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a537928a84f210158191ea44ca58ee8e.html "Returns an unsigned 64-bit value containing the bit length of the column parameter.") :arrow_upper_right:

