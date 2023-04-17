<!-- loio4140080f259d4f1a9fc85ce11cab8d55 -->

# ISNULL Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the value of the first non-NULL expression in the parameter list.



```
ISNULL ( <expression>, <expression> [ …, <expression> ] )
```



<a name="loio4140080f259d4f1a9fc85ce11cab8d55__section_y4v_kmh_trb"/>

## Parameters

 *<expression\>*
 :   An expression to be tested against NULL.

 

<a name="loio4140080f259d4f1a9fc85ce11cab8d55__section_b2k_lmh_trb"/>

## Returns

The return type for this function depends on the expressions specified. That is, when the database server evaluates the function, it first searches for a data type in which all the expressions can be compared. When found, the database server compares the expressions and then returns the result in the type used for the comparison. If the database server cannot find a common comparison type, an error is returned.



<a name="loio4140080f259d4f1a9fc85ce11cab8d55__section_mbf_mmh_trb"/>

## Remarks

At least two expressions must be passed to the function.

The ISNULL function is the same as the COALESCE function.



<a name="loio4140080f259d4f1a9fc85ce11cab8d55__section_ml2_fnh_trb"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loio4140080f259d4f1a9fc85ce11cab8d55__section_at4_fnh_trb"/>

## Example

The following statement returns the value -66:

```
SELECT ISNULL( NULL ,-66, 55, 45, NULL, 16 ) FROM iq_dummy
```

**Related Information**  


[ISNULL Function [Miscellaneous] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a55a73cd84f21015ae0b9236251e12e7.html "Returns the value of the first non-NULL expression in the parameter list.") :arrow_upper_right:

