<!-- loioa5638af584f210158d1fe90a3fb7c0ec -->

# MIN Function \[Aggregate\] for Data Lake Relational Engine

Returns the minimum expression value found in each group of rows.



```
MIN ( <expression>
| DISTINCT <column-name> );
```



<a name="loioa5638af584f210158d1fe90a3fb7c0ec__MIN_parm1"/>

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



<a name="loioa5638af584f210158d1fe90a3fb7c0ec__MIN_returns1"/>

## Result Set

The same data type as the argument.



<a name="loioa5638af584f210158d1fe90a3fb7c0ec__MIN_remarks1"/>

## Remarks

Rows where *<expression\>* is NULL are ignored. Returns NULL for a group containing no rows.



<a name="loioa5638af584f210158d1fe90a3fb7c0ec__MIN_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa5638af584f210158d1fe90a3fb7c0ec__MIN_examples1"/>

## Examples

The following statement returns the value 24903.000, representing the minimum salary in the Employees table:

```
SELECT MIN ( Salary )
FROM Employees;
```

**Related Information**  


[Windowing Aggregate Function Usage in Data Lake Relational Engine](windowing-aggregate-function-usage-in-data-lake-relational-engine-a527f35.md "A major feature of the ISO/ANSI SQL extensions for OLAP is a construct called a window.")

[MAX Function \[Aggregate\] for Data Lake Relational Engine](max-function-aggregate-for-data-lake-relational-engine-a5626d6.md "Returns the maximum expression value found in each group of rows.")

[MIN Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/6cfcb760c23641ab9c5aaa17d056f4c0.html "Returns the minimum expression value found in each group of rows.") :arrow_upper_right:

