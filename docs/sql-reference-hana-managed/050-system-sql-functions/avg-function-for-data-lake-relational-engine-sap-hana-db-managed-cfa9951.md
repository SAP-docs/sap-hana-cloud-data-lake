<!-- loiocfa9951f7f2849798b476c280c824ffb -->

# AVG Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.



```
AVG ( <numeric-expression> | DISTINCT <column-name>);
```



<a name="loiocfa9951f7f2849798b476c280c824ffb__section_ag3_ghk_srb"/>

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



<a name="loiocfa9951f7f2849798b476c280c824ffb__section_ltc_hhk_srb"/>

## Result Set

Returns the NULL value for a group containing no rows.

Returns DOUBLE if the argument is DOUBLE, otherwise NUMERIC.



<a name="loiocfa9951f7f2849798b476c280c824ffb__section_y1t_hhk_srb"/>

## Remarks

This average does not include rows where *<numeric-expression\>* is the NULL value. Returns the NULL value for a group containing no rows.



<a name="loiocfa9951f7f2849798b476c280c824ffb__section_ph3_3hk_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loiocfa9951f7f2849798b476c280c824ffb__section_jzh_jhk_srb"/>

## Example

The following statement returns the value 49988.6:

```
SELECT AVG ( salary ) FROM Employees;
```

**Related Information**  


[AVG Function \[Aggregate\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a535f04784f2101590f89a693842c970.html "Computes the average of a numeric expression for a set of rows, or computes the average of a set of unique values.") :arrow_upper_right:

