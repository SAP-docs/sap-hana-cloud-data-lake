<!-- loioa569fd1184f210159b61c1d4823ce243 -->

# NULLIF Function \[Miscellaneous\] for Data Lake Relational Engine

Provides an abbreviated `CASE` expression by comparing expressions.



```
NULLIF ( <expression1>, <expression2> )
```



<a name="loioa569fd1184f210159b61c1d4823ce243__NULLIF_parm1"/>

## Parameters

 *<expression1\>*
 :   An expression to be compared.

  *<expression2\>*
 :   An expression to be compared.

 

<a name="loioa569fd1184f210159b61c1d4823ce243__NULLIF_returns1"/>

## Returns

Data type of the first argument.



<a name="loioa569fd1184f210159b61c1d4823ce243__NULLIF_remarks1"/>

## Remarks

`NULLIF` compares the values of the two expressions.

If the first expression equals the second expression, `NULLIF`returns NULL.

If the first expression does not equal the second expression, or if the second expression is NULL, `NULLIF` returns the first expression.

The `NULLIF` function provides a short way to write some `CASE` expressions. `NULLIF` is equivalent to:

```
CASE WHEN <expression1> = <expression2> THEN NULL 
ELSE <expression1> END
```



<a name="loioa569fd1184f210159b61c1d4823ce243__NULLIF_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa569fd1184f210159b61c1d4823ce243__NULLIF_examples1"/>

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


[CASE Expressions in Data Lake Relational Engine](../010-sql-language-elements/case-expressions-in-data-lake-relational-engine-a4f6a6f.md "The CASE expression provides conditional SQL expressions.")

[NULLIF Function for Abbreviated CASE Expressions in Data Lake Relational Engine](../010-sql-language-elements/nullif-function-for-abbreviated-case-expressions-in-data-lake-relational-engine-a4f7256.md "The NULLIF function provides a way to write some CASE statements in short form.")

[NULLIF Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/601a225cec8f4647a3a612f92994e087.html "Provides an abbreviated CASE expression by comparing expressions.") :arrow_upper_right:

