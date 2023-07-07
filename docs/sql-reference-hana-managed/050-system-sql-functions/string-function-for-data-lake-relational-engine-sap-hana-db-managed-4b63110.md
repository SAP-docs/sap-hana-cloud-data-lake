<!-- loio4b6311065965472286c536537d380f53 -->

# STRING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Concatenates one or more strings into one large string.



```
STRING ( <string-expression> [ , … ] )
```



```
STRING ( <string-expression> [ , … ] )
```



<a name="loio4b6311065965472286c536537d380f53__section_b5s_t43_wrb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

A string. If only one argument is supplied, it is converted into a single expression. If more than one argument is supplied, they are concatenated into a single string. A NULL is treated as an empty string \(''\).



</dd>
</dl>



<a name="loio4b6311065965472286c536537d380f53__section_i1g_543_wrb"/>

## Returns

-   LONG BINARY
-   LONG NVARCHAR
-   LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `STRING` in a `SELECT INTO` statement, you must use `CAST` and set `STRING` to the correct data type and size.



<a name="loio4b6311065965472286c536537d380f53__section_o2v_543_wrb"/>

## Remarks

Numeric or date parameters are converted to strings before concatenation. You can also use the `STRING` function to convert any single expression to a string by supplying that expression as the only parameter.

If all parameters are NULL, `STRING` returns NULL.



<a name="loio4b6311065965472286c536537d380f53__section_zrj_v43_wrb"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio4b6311065965472286c536537d380f53__section_pcy_zs5_vrb"/>

## Example

The following statement returns the value testing123:

```
SELECT STRING( 'testing', NULL, 123 )
FROM iq_dummy
```

**Related Information**  


[STRING Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a586010d84f210158657b25cdb264bf0.html "Concatenates one or more strings into one large string.") :arrow_upper_right:

