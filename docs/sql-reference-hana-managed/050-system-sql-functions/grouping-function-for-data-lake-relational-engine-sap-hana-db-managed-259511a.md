<!-- loio259511aa310241949d6e8389561dc62c -->

# GROUPING Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Identifies whether a column in a `ROLLUP` or `CUBE` operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.



```
GROUPING ( <group-by-expression> ); 
```



<a name="loio259511aa310241949d6e8389561dc62c__section_x12_bqg_trb"/>

## Parameters


<dl>
<dt><b>

*<group-by-expression\>*

</b></dt>
<dd>

An expression appearing as a grouping column in the result set of a query that uses a GROUP BY clause with the ROLLUP or CUBE keyword. The function identifies subtotal rows added to the result set by a ROLLUP or CUBE operation.



</dd>
</dl>



<a name="loio259511aa310241949d6e8389561dc62c__section_ayp_bqg_trb"/>

## Result Set

-   1 – indicates that *<group-by-expression\>* is NULL because it is part of a subtotal row. The column is not a prefix column for that row.
-   0 – indicates that *<group-by-expression\>* is a prefix column of a subtotal row.



<a name="loio259511aa310241949d6e8389561dc62c__section_nm2_cqg_trb"/>

## Remarks

Data lake Relational Engine does not support the PERCENTILE\_CONT or PERCENTILE\_DISC functions with GROUP BY CUBE operations.



<a name="loio259511aa310241949d6e8389561dc62c__section_ugp_cqg_trb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar

**Related Information**  


[GROUP BY Clause for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/group-by-clause-for-data-lake-relational-engine-sap-hana-db-managed-86be6d9.md)

[GROUPING Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a554461384f21015aca0af2a35f9c2a7.html "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.") :arrow_upper_right:

