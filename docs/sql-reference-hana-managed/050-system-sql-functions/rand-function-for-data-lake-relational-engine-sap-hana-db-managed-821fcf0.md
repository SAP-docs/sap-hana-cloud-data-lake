<!-- loio821fcf0e2d12450185efac750f617450 -->

# RAND Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a `DOUBLE` precision, random number x, where 0 <= x <1, with an optional seed.



```
RAND ( [ <integer-expression> ] );
```



<a name="loio821fcf0e2d12450185efac750f617450__section_rvv_nm5_vrb"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The optional seed used to create a random number. This argument allows you to create repeatable random number sequences.



</dd>
</dl>



<a name="loio821fcf0e2d12450185efac750f617450__section_ws3_4m5_vrb"/>

## Result Set

DOUBLE



<a name="loio821fcf0e2d12450185efac750f617450__section_rlr_4m5_vrb"/>

## Remarks

If `RAND` is called with a `FROM` clause and an argument in a query containing only tables in IQ stores, the function returns an arbitrary but repeatable value.

When no argument is called, `RAND` is a non-deterministic function. Successive calls to `RAND` might return different values. The query optimizer does not cache the results of the `RAND` function

> ### Note:  
> The values returned by `RAND` vary depending on whether you use a `FROM` clause or not and whether the referenced table was created in `SYSTEM` or in an IQ store.



<a name="loio821fcf0e2d12450185efac750f617450__section_ymm_pm5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio821fcf0e2d12450185efac750f617450__section_wby_pm5_vrb"/>

## Examples

-   The following statement returns a 5% sampling of a table:

    ```
    SELECT AVG(table1.number_of_cars), 
        AVG(table1.number_of_tvs)FROM table1 WHERE 
        RAND(ROWID(table1)) < .05 and table1.income < 50000;
    ```

-   The following statement returns a value of approximately 941392926249216914:

    ```
    SELECT RAND( 4 ) FROM iq_dummy;
    ```


**Related Information**  


[RAND Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a572b2db84f210159574b044cfd9dcb6.html "Returns a DOUBLE precision, random number x, where 0 <= x <1, with an optional seed.") :arrow_upper_right:

