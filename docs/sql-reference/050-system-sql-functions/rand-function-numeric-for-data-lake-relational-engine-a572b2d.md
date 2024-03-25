<!-- loioa572b2db84f210159574b044cfd9dcb6 -->

# RAND Function \[Numeric\] for Data Lake Relational Engine

Returns a `DOUBLE` precision, random number x, where 0 <= x <1, with an optional seed.



```
RAND ( [ <integer-expression> ] );
```



<a name="loioa572b2db84f210159574b044cfd9dcb6__RAND_parm1"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The optional seed used to create a random number. This argument allows you to create repeatable random number sequences.



</dd>
</dl>



<a name="loioa572b2db84f210159574b044cfd9dcb6__RAND_returns1"/>

## Result Set

DOUBLE



<a name="loioa572b2db84f210159574b044cfd9dcb6__RAND_remarks1"/>

## Remarks

If `RAND` is called with a `FROM` clause and an argument in a query containing only tables in IQ stores, the function returns an arbitrary but repeatable value.

When no argument is called, `RAND` is a non-deterministic function. Successive calls to `RAND` might return different values. The query optimizer does not cache the results of the `RAND` function

> ### Note:  
> The values returned by `RAND` vary depending on whether you use a `FROM` clause or not and whether the referenced table was created in `SYSTEM` or in an IQ store.



<a name="loioa572b2db84f210159574b044cfd9dcb6__RAND_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa572b2db84f210159574b044cfd9dcb6__RAND_examples1"/>

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


[RAND Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/821fcf0e2d12450185efac750f617450.html "Returns a DOUBLE precision, random number x, where 0 <= x <1, with an optional seed.") :arrow_upper_right:

