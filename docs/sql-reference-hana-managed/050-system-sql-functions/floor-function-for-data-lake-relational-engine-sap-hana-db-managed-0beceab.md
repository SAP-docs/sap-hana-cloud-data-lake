<!-- loio0beceabbce184f14a1a3fd1482727a2d -->

# FLOOR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the floor of \(largest integer not greater than\) a number.



```
FLOOR ( <numeric-expression> )
```



<a name="loio0beceabbce184f14a1a3fd1482727a2d__section_obh_tqg_trb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The number, usually a float.



</dd>
</dl>



<a name="loio0beceabbce184f14a1a3fd1482727a2d__section_ast_tqg_trb"/>

## Returns

DOUBLE



<a name="loio0beceabbce184f14a1a3fd1482727a2d__section_pr2_5qg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio0beceabbce184f14a1a3fd1482727a2d__section_h2t_5qg_trb"/>

## Examples

-   The following statement returns the value 123.00:

    ```
    SELECT FLOOR ( 123 ) FROM iq_dummy
    ```

-   The following statement returns the value 123:

    ```
    SELECT FLOOR ( 123.45 ) FROM iq_dummy
    ```

-   The following statement returns the value -124.00:

    ```
    SELECT FLOOR ( -123.45 ) FROM iq_dummy
    ```


**Related Information**  


[FIRST\_VALUE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](first-value-function-for-data-lake-relational-engine-sap-hana-db-managed-9994e0a.md "Returns the first value from a set of values.")

[FLOOR Function [Numeric] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a552c1cc84f21015bfc3d6309d6785d6.html "Returns the floor of (largest integer not greater than) a number.") :arrow_upper_right:

