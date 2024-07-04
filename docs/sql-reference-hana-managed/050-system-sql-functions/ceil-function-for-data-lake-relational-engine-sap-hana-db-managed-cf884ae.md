<!-- loiocf884aecfedf41a49b65a4082fa91ffa -->

# CEIL Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the smallest integer greater than or equal to the specified expression.



```
CEIL ( <numeric-expression> );
```



<a name="loiocf884aecfedf41a49b65a4082fa91ffa__section_ygc_35l_srb"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

A column, variable, or expression with a data type that is either exact numeric, approximate numeric, money, or any type that can be implicitly converted to one of these types. For other data types, `CEIL` generates an error. The return value has the same data type as the value supplied.



</dd>
</dl>



<a name="loiocf884aecfedf41a49b65a4082fa91ffa__section_j3r_35l_srb"/>

## Remarks

`CEIL` is as synonym for `CEILING`.

For a given expression, the `CEIL` function takes one argument. For example, `CEIL (-123.45)` returns `-123`. `CEIL (123.45)` returns `124`.



<a name="loiocf884aecfedf41a49b65a4082fa91ffa__section_gff_j5l_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant

**Related Information**  


[CEILING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](ceiling-function-for-data-lake-relational-engine-sap-hana-db-managed-2201fad.md "Returns the ceiling (smallest integer not less than) of a number.")

[FLOOR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](floor-function-for-data-lake-relational-engine-sap-hana-db-managed-0beceab.md "Returns the floor of (largest integer not greater than) a number.")

[CEIL Function \[Numeric\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a53a419c84f21015b689e542cbf26996.html "Returns the smallest integer greater than or equal to the specified expression.") :arrow_upper_right:

