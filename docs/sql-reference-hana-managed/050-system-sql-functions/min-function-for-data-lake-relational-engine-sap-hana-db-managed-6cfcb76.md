<!-- loio6cfcb760c23641ab9c5aaa17d056f4c0 -->

# MIN Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the minimum expression value found in each group of rows.



```
MIN ( <expression>
| DISTINCT <column-name> );
```



<a name="loio6cfcb760c23641ab9c5aaa17d056f4c0__section_hjt_2hn_vrb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression for which the minimum value is to be calculated. This is commonly a column name.



</dd><dt><b>

DISTINCT *<column-name\>*

</b></dt>
<dd>

Returns the same as <code>MIN ( <i class="varname">&lt;expression&gt;</i> )</code>, and is included for completeness.



</dd>
</dl>



<a name="loio6cfcb760c23641ab9c5aaa17d056f4c0__section_b1k_fhn_vrb"/>

## Result Set

The same data type as the argument.



<a name="loio6cfcb760c23641ab9c5aaa17d056f4c0__section_uqr_hhn_vrb"/>

## Remarks

Rows where *<expression\>* is NULL are ignored. Returns NULL for a group containing no rows.



<a name="loio6cfcb760c23641ab9c5aaa17d056f4c0__section_rdd_3hn_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loio6cfcb760c23641ab9c5aaa17d056f4c0__section_dn2_jhn_vrb"/>

## Examples

The following statement returns the value 24903.000, representing the minimum salary in the Employees table:

```
SELECT MIN ( Salary )
FROM Employees;
```

**Related Information**  


[MIN Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a5638af584f210158d1fe90a3fb7c0ec.html "Returns the minimum expression value found in each group of rows.") :arrow_upper_right:

