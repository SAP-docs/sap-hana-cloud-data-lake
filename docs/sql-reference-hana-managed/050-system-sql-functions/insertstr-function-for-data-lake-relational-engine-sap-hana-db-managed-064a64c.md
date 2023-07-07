<!-- loio064a64ca374142608c2c968248d9bbe7 -->

# INSERTSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Inserts a string into another string at a specified position.



```
INSERTSTR ( <numeric-expression>, <string-expression1>, <string-expression2> )
```



<a name="loio064a64ca374142608c2c968248d9bbe7__section_h5m_z4h_trb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The position after which *<string-expression2\>* is to be inserted. Use zero to insert a string at the beginning.



</dd><dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The string into which *<string-expression2\>* is to be inserted.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The string to be inserted.



</dd>
</dl>



<a name="loio064a64ca374142608c2c968248d9bbe7__section_ez1_1ph_trb"/>

## Returns

LONG VARCHAR or LONG BINARY, depending on the data type of the input expressions.

> ### Note:  
> The result data type is a LONG VARCHAR. If you use `INSERTSTR` in a `SELECT INTO` statement, you must use `CAST` and set `INSERTSTR` to the correct data type and size.



<a name="loio064a64ca374142608c2c968248d9bbe7__section_znr_1ph_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.



<a name="loio064a64ca374142608c2c968248d9bbe7__section_scc_bph_trb"/>

## Example

The following statement returns the value "backoffice":

```
SELECT INSERTSTR( 0, 'office ', 'back' ) FROM iq_dummy
```

**Related Information**  


[INSERTSTR Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a558efff84f210159092915333b9e6df.html "Inserts a string into another string at a specified position.") :arrow_upper_right:

