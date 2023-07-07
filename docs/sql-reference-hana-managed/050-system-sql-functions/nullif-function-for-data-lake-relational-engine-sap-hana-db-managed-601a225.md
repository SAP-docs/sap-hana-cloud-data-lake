<!-- loio601a225cec8f4647a3a612f92994e087 -->

# NULLIF Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Provides an abbreviated `CASE` expression by comparing expressions.



```
NULLIF ( <expression1>, <expression2> )
```



<a name="loio601a225cec8f4647a3a612f92994e087__section_jyb_2nn_vrb"/>

## Parameters


<dl>
<dt><b>

*<expression1\>*

</b></dt>
<dd>

An expression to be compared.



</dd><dt><b>

*<expression2\>*

</b></dt>
<dd>

An expression to be compared.



</dd>
</dl>



<a name="loio601a225cec8f4647a3a612f92994e087__section_vns_2nn_vrb"/>

## Returns

Data type of the first argument.



<a name="loio601a225cec8f4647a3a612f92994e087__section_u3b_fnn_vrb"/>

## Remarks

`NULLIF` compares the values of the two expressions.

If the first expression equals the second expression, `NULLIF`returns NULL.

If the first expression does not equal the second expression, or if the second expression is NULL, `NULLIF` returns the first expression.

The `NULLIF` function provides a short way to write some `CASE` expressions. `NULLIF` is equivalent to:

```
CASE WHEN <expression1> = <expression2> THEN NULL 
ELSE <expression1> END
```



<a name="loio601a225cec8f4647a3a612f92994e087__section_ths_fnn_vrb"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio601a225cec8f4647a3a612f92994e087__section_dpg_gnn_vrb"/>

## Examples

-   The following statement returns `a`:

    ```
    SELECT NULLIF( 'a', 'b' ) FROM iq_dummy
    ```

-   The following statement returns NULL:

    ```
    SELECT NULLIF( 'a', 'a' ) FROM iq_dummy
    ```


**Related Information**  


[NULLIF Function [Miscellaneous] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a569fd1184f210159b61c1d4823ce243.html "Provides an abbreviated CASE expression by comparing expressions.") :arrow_upper_right:

