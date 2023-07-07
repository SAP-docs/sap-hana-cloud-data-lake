<!-- loioad081410a2bf423c888257b5d0f621a3 -->

# SPACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns a specified number of spaces.



```
SPACE ( <integer-expression> )
```



<a name="loioad081410a2bf423c888257b5d0f621a3__section_t33_gx5_vrb"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number of spaces to return.



</dd>
</dl>



<a name="loioad081410a2bf423c888257b5d0f621a3__section_bpv_gx5_vrb"/>

## Returns

LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `SPACE` in a `SELECT INTO` statement, you must use `CAST` and set `SPACE` to the correct data type and size.



<a name="loioad081410a2bf423c888257b5d0f621a3__section_qyl_hx5_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioad081410a2bf423c888257b5d0f621a3__section_zpf_3x5_vrb"/>

## Example

The following statement returns a string containing 10 spaces:

```
SELECT SPACE( 10 ) FROM iq_dummy
```

**Related Information**  


[SPACE Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5815e2c84f210158cf48f3c618df22c.html "Returns a specified number of spaces.") :arrow_upper_right:

