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


 <?sap-ot O2O class="- topic/link " href="86be6d9a901f4b1ca1977a88cc39b545.xml" text="" desc="" xtrc="link:1" xtrf="file:/home/builder/src/dita-all/vmv1718848528851/loioebf3112b870e474d9a791e9427bc62e1_en-US/src/content/localization/en-us/259511aa310241949d6e8389561dc62c.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

[GROUPING Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a554461384f21015aca0af2a35f9c2a7.html "Identifies whether a column in a ROLLUP or CUBE operation result set is NULL because it is part of a subtotal row, or NULL because of the underlying data.") :arrow_upper_right:

