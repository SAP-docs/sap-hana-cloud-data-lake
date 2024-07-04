<!-- loioae1f29e228714cf085d6eb1d0ee075f8 -->

# MAX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the maximum *<expression\>* value found in each group of rows.



```
MAX ( <expression>
| DISTINCT <column-name> );
```



<a name="loioae1f29e228714cf085d6eb1d0ee075f8__section_idh_43n_vrb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The expression for which the maximum value is to be calculated. This is commonly a column name.



</dd><dt><b>

DISTINCT *<column-name\>*

</b></dt>
<dd>

Returns the same as <code>MAX ( <i class="varname">&lt;expression&gt;</i> )</code>, and is included for completeness.



</dd>
</dl>



<a name="loioae1f29e228714cf085d6eb1d0ee075f8__section_h3c_p3n_vrb"/>

## Result Set

The same data type as the argument.



<a name="loioae1f29e228714cf085d6eb1d0ee075f8__section_xvm_p3n_vrb"/>

## Remarks

Rows where *<expression\>* is NULL are ignored. Returns NULL for a group containing no rows.



<a name="loioae1f29e228714cf085d6eb1d0ee075f8__section_fty_p3n_vrb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioae1f29e228714cf085d6eb1d0ee075f8__section_svc_r3n_vrb"/>

## Examples

The following statement returns the value 138948.000, representing the maximum salary in the Employees table:

```
SELECT MAX ( Salary )
FROM Employees;
```

**Related Information**  


[MAX Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a5626d6684f210158cafad316e131142.html "Returns the maximum expression value found in each group of rows.") :arrow_upper_right:

