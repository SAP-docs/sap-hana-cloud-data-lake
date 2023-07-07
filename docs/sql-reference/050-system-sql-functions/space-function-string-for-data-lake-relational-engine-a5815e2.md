<!-- loioa5815e2c84f210158cf48f3c618df22c -->

# SPACE Function \[String\] for Data Lake Relational Engine

Returns a specified number of spaces.



```
SPACE ( <integer-expression> )
```



<a name="loioa5815e2c84f210158cf48f3c618df22c__SPACE_parm1"/>

## Parameters


<dl>
<dt><b>

*<integer-expression\>*

</b></dt>
<dd>

The number of spaces to return.



</dd>
</dl>



<a name="loioa5815e2c84f210158cf48f3c618df22c__SPACE_returns1"/>

## Returns

LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `SPACE` in a `SELECT INTO` statement, you must use `CAST` and set `SPACE` to the correct data type and size.



<a name="loioa5815e2c84f210158cf48f3c618df22c__SPACE_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loioa5815e2c84f210158cf48f3c618df22c__SPACE_example1"/>

## Example

The following statement returns a string containing 10 spaces:

```
SELECT SPACE( 10 ) FROM iq_dummy
```

**Related Information**  


[SPACE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/ad081410a2bf423c888257b5d0f621a3.html "Returns a specified number of spaces.") :arrow_upper_right:

