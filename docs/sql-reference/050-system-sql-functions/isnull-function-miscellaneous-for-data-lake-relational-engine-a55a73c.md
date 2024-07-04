<!-- loioa55a73cd84f21015ae0b9236251e12e7 -->

# ISNULL Function \[Miscellaneous\] for Data Lake Relational Engine

Returns the value of the first non-NULL expression in the parameter list.



```
ISNULL ( <expression>, <expression> [ …, <expression> ] );
```



<a name="loioa55a73cd84f21015ae0b9236251e12e7__ISNULL_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

An expression to be tested against NULL.



</dd>
</dl>



<a name="loioa55a73cd84f21015ae0b9236251e12e7__ISNULL_returns1"/>

## Result Set

The return type for this function depends on the expressions specified. That is, when the database server evaluates the function, it first searches for a data type in which all the expressions can be compared. When found, the database server compares the expressions and then returns the result in the type used for the comparison. If the database server cannot find a common comparison type, an error is returned.



<a name="loioa55a73cd84f21015ae0b9236251e12e7__ISNULL_remarks1"/>

## Remarks

At least two expressions must be passed to the function.

The ISNULL function is the same as the COALESCE function.



<a name="loioa55a73cd84f21015ae0b9236251e12e7__ISNULL_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa55a73cd84f21015ae0b9236251e12e7__ISNULL_example1"/>

## Examples

The following statement returns the value -66:

```
SELECT ISNULL( NULL ,-66, 55, 45, NULL, 16 ) FROM iq_dummy;
```

**Related Information**  


[COALESCE Function \[Miscellaneous\] for Data Lake Relational Engine](coalesce-function-miscellaneous-for-data-lake-relational-engine-a53d627.md "Returns the first non-NULL expression from a list.")

[ISNULL Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/4140080f259d4f1a9fc85ce11cab8d55.html "Returns the value of the first non-NULL expression in the parameter list.") :arrow_upper_right:

