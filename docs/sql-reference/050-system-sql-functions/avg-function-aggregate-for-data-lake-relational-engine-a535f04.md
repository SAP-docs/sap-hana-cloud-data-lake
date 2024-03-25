<!-- loioa535f04784f2101590f89a693842c970 -->

# AVG Function \[Aggregate\] for Data Lake Relational Engine

Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.



```
AVG ( <numeric-expression> | DISTINCT <column-name>);
```



<a name="loioa535f04784f2101590f89a693842c970__AVG_parm1"/>

## Parameters


<dl>
<dt><b>

*<numeric-expression\>*

</b></dt>
<dd>

The value that is the average calculated over a set of rows.



</dd><dt><b>

DISTINCT *<column-name\>*

</b></dt>
<dd>

Computes the average of the unique values in *<column-name\>*. This is of limited usefulness, but provides for completeness



</dd>
</dl>



<a name="loioa535f04784f2101590f89a693842c970__AVG_returns1"/>

## Result Set

Returns the NULL value for a group containing no rows.

Returns DOUBLE if the argument is DOUBLE, otherwise NUMERIC.



<a name="loioa535f04784f2101590f89a693842c970__AVG_remarks1"/>

## Remarks

This average does not include rows where *<numeric-expression\>* is the NULL value. Returns the NULL value for a group containing no rows.



<a name="loioa535f04784f2101590f89a693842c970__AVG_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa535f04784f2101590f89a693842c970__AVG_example1"/>

## Example

The following statement returns the value 49988.6:

```
SELECT AVG ( salary ) FROM Employees;
```

**Related Information**  


[AVG Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/cfa9951f7f2849798b476c280c824ffb.html "Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.") :arrow_upper_right:

