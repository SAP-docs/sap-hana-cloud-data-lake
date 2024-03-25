<!-- loio4af5411816c4466b9335a79034b00833 -->

# COALESCE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the first non-NULL expression from a list.



```
COALESCE ( <expression>, <expression> [ , … ] );
```



<a name="loio4af5411816c4466b9335a79034b00833__section_x3k_4rl_srb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Any expression.



</dd>
</dl>



<a name="loio4af5411816c4466b9335a79034b00833__section_gfy_4rl_srb"/>

## Result Set

ANY



<a name="loio4af5411816c4466b9335a79034b00833__section_ibq_prl_srb"/>

## Standards and Compatibility

-   SQL – ISO/ANSI SQL compliant



<a name="loio4af5411816c4466b9335a79034b00833__section_um2_qrl_srb"/>

## Example

The following statement returns the value 34:

```
SELECT COALESCE( NULL, 34, 13, 0 ) FROM iq_dummy;
```

**Related Information**  


[COALESCE Function \[Miscellaneous\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a53d627984f21015a1fa9a5eb36a5dde.html "Returns the first non-NULL expression from a list.") :arrow_upper_right:

