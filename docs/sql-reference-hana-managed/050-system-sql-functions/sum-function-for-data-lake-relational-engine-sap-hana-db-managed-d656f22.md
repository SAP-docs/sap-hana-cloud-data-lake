<!-- loiod656f224db9a4567a7ba604993702e94 -->

# SUM Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the total of the specified expression for each group of rows.



```
SUM ( <expression> | DISTINCT <column-name> )
```



<a name="loiod656f224db9a4567a7ba604993702e94__section_tzl_lq5_vrb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The object to be summed. This is commonly a column name.



</dd><dt><b>

DISTINCT *<column-name\>*

</b></dt>
<dd>

Computes the sum of the unique values in *<column-name\>* for each group of rows. This is of limited usefulness, but is included for completeness.



</dd>
</dl>



<a name="loiod656f224db9a4567a7ba604993702e94__section_kkv_lq5_vrb"/>

## Returns

-   INTEGER
-   DOUBLE
-   NUMERIC
-   BIGINT \(SIGNED or UNSIGNED\)



<a name="loiod656f224db9a4567a7ba604993702e94__section_v1k_mq5_vrb"/>

## Remarks

Rows where the specified expression is NULL are not included.

Returns NULL for a group containing no rows.



<a name="loiod656f224db9a4567a7ba604993702e94__section_ejv_mq5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loiod656f224db9a4567a7ba604993702e94__section_ylf_nq5_vrb"/>

## Example

The following statement returns the value 3749146.740:

```
SELECT SUM( salary )
FROM Employees
```

**Related Information**  


[SUM Function [Aggregate] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5889fe484f21015b024abf6dcede473.html "Returns the total of the specified expression for each group of rows.") :arrow_upper_right:

