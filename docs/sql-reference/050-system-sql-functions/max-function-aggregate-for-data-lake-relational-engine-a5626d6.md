<!-- loioa5626d6684f210158cafad316e131142 -->

# MAX Function \[Aggregate\] for Data Lake Relational Engine

Returns the maximum *<expression\>* value found in each group of rows.



```
MAX ( <expression>
| DISTINCT <column-name> );
```



<a name="loioa5626d6684f210158cafad316e131142__MAX_parm1"/>

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



<a name="loioa5626d6684f210158cafad316e131142__MAX_returns1"/>

## Result Set

The same data type as the argument.



<a name="loioa5626d6684f210158cafad316e131142__MAX_remarks1"/>

## Remarks

Rows where *<expression\>* is NULL are ignored. Returns NULL for a group containing no rows.



<a name="loioa5626d6684f210158cafad316e131142__MAX_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa5626d6684f210158cafad316e131142__MAX_example1"/>

## Examples

The following statement returns the value 138948.000, representing the maximum salary in the Employees table:

```
SELECT MAX ( Salary )
FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[MIN Function \[Aggregate\] for Data Lake Relational Engine](min-function-aggregate-for-data-lake-relational-engine-a5638af.md "Returns the minimum expression value found in each group of rows.")

[MAX Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/ae1f29e228714cf085d6eb1d0ee075f8.html "Returns the maximum expression value found in each group of rows.") :arrow_upper_right:

