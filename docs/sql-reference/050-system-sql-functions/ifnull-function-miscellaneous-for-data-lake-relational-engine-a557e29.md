<!-- loioa557e29b84f21015b460f69ff0fed6da -->

# IFNULL Function \[Miscellaneous\] for Data Lake Relational Engine

Returns the first non-null expression, or NULL.



```
IFNULL ( <expression1>, <expression2> [ , <expression3> ] );
```



<a name="loioa557e29b84f21015b460f69ff0fed6da__IFNULL_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression1\>*

</b></dt>
<dd>

The expression to be evaluated. Its value determines whether *<expression2\>* or *<expression3\>* is returned.



</dd><dt><b>

*<expression2\>*

</b></dt>
<dd>

The return value if *<expression1\>* is NULL



</dd><dt><b>

*<expression3\>*

</b></dt>
<dd>

\(Optional\) The return value if *<expression1\>* is not NULL.



</dd>
</dl>



<a name="loioa557e29b84f21015b460f69ff0fed6da__IFNULL_returns1"/>

## Result Set

The data type returned depends on the data type of *<expression2\>* and *<expression3\>*.



<a name="loioa557e29b84f21015b460f69ff0fed6da__IFNULL_remarks1"/>

## Remarks

If the first expression is the NULL value, then the value of the second expression is returned. If the first expression is not NULL, the value of the third expression is returned. If the first expression is not NULL and there is no third expression, then the NULL value is returned.



<a name="loioa557e29b84f21015b460f69ff0fed6da__IFNULL_standards1"/>

## Standards and compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa557e29b84f21015b460f69ff0fed6da__IFNULL_example1"/>

## Examples

-   The following statement returns the value expression: -66:

    ```
    SELECT IFNULL( NULL, -66 ) FROM iq_dummy;
    ```

-   The following statement returns NULL, because the first expression isn’t NULL and there’s no third:

    ```
    SELECT IFNULL( -66, -66 ) FROM iq_dummy;
    ```


**Related Information**  


[IFNULL Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/059555a4b6fd4824851aa1d544d77a10.html "Returns the first non-null expression, or NULL.") :arrow_upper_right:

