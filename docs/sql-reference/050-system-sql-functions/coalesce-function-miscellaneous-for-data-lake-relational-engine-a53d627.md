<!-- loioa53d627984f21015a1fa9a5eb36a5dde -->

# COALESCE Function \[Miscellaneous\] for Data Lake Relational Engine

Returns the first non-NULL expression from a list.



```
COALESCE ( <expression>, <expression> [ , … ] );
```



<a name="loioa53d627984f21015a1fa9a5eb36a5dde__COALESCE_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Any expression.



</dd>
</dl>



<a name="loioa53d627984f21015a1fa9a5eb36a5dde__COALESCE_returns1"/>

## Result Set

ANY



<a name="loioa53d627984f21015a1fa9a5eb36a5dde__COALESCE_standards1"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loioa53d627984f21015a1fa9a5eb36a5dde__COALESCE_examples"/>

## Example

The following statement returns the value 34:

```
SELECT COALESCE( NULL, 34, 13, 0 ) FROM iq_dummy;
```

**Related Information**  


[ISNULL Function \[Miscellaneous\] for Data Lake Relational Engine](isnull-function-miscellaneous-for-data-lake-relational-engine-a55a73c.md "Returns the value of the first non-NULL expression in the parameter list.")

[COALESCE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/4af5411816c4466b9335a79034b00833.html "Returns the first non-NULL expression from a list.") :arrow_upper_right:

