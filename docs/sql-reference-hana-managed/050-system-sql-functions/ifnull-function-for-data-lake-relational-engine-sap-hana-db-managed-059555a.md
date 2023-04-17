<!-- loio059555a4b6fd4824851aa1d544d77a10 -->

# IFNULL Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the first non-null expression, or NULL.



```
IFNULL ( <expression1>, <expression2> [ , <expression3> ] )
```



<a name="loio059555a4b6fd4824851aa1d544d77a10__section_qrj_jph_trb"/>

## Parameters

 *<expression1\>*
 :   The expression to be evaluated. Its value determines whether *<expression2\>* or *<expression3\>* is returned.

  *<expression2\>*
 :   The return value if *<expression1\>* is NULL

  *<expression3\>*
 :   \(Optional\) The return value if *<expression1\>* is not NULL.

 

<a name="loio059555a4b6fd4824851aa1d544d77a10__section_ibx_jph_trb"/>

## Returns

The data type returned depends on the data type of *<expression2\>* and *<expression3\>*.



<a name="loio059555a4b6fd4824851aa1d544d77a10__section_ivk_kph_trb"/>

## Remarks

If the first expression is the NULL value, then the value of the second expression is returned. If the first expression is not NULL, the value of the third expression is returned. If the first expression is not NULL and there is no third expression, then the NULL value is returned.



<a name="loio059555a4b6fd4824851aa1d544d77a10__section_a45_kph_trb"/>

## Standards and compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loio059555a4b6fd4824851aa1d544d77a10__section_ath_nph_trb"/>

## Examples

-   The following statement returns the value expression: -66:

    ```
    SELECT IFNULL( NULL, -66 ) FROM dbo.iq_dummy;
    ```

-   The following statement returns NULL, because the first expression isn’t NULL and there’s no third:

    ```
    SELECT IFNULL( -66, -66 ) FROM dbo.iq_dummy;
    ```


**Related Information**  


[IFNULL Function [Miscellaneous] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a557e29b84f21015b460f69ff0fed6da.html "Returns the first non-null expression, or NULL.") :arrow_upper_right:

