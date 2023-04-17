<!-- loio5572345aa04d4c2fbd9b9589ed18e296 -->

# STRTOUUID Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts a string value to a unique identifier \(UUID or GUID\) value.



```
STRTOUUID ( <string-expression> ) 
```



<a name="loio5572345aa04d4c2fbd9b9589ed18e296__section_tdp_3s5_vrb"/>

## Parameters

  *<string-expression\>* 
 :   A string in the format *<xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\>*

 

<a name="loio5572345aa04d4c2fbd9b9589ed18e296__section_oc2_js5_vrb"/>

## Returns

UNIQUEIDENTIFIER



<a name="loio5572345aa04d4c2fbd9b9589ed18e296__section_pcn_js5_vrb"/>

## Remarks

Converts a string in the format *<xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\>* where *<x\>* is a hexadecimal digit, to a unique identifier value. If the string is not a valid UUID string, NULL is returned.

You can use `STRTOUUID` to insert UUID values into a data lake Relational Engine database.



<a name="loio5572345aa04d4c2fbd9b9589ed18e296__section_qs1_ks5_vrb"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio5572345aa04d4c2fbd9b9589ed18e296__section_hdk_ks5_vrb"/>

## Example

```
CREATE TABLE T (
 pk uniqueidentifier primary key,
 c1 int); 
INSERT INTO T (pk, c1)
 VALUES (STRTOUUID
 ('12345678-1234-5678-9012-123456789012'), 1);
```

**Related Information**  


[STRTOUUID Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58683c184f21015bb5cb68f114bbcb9.html "Converts a string value to a unique identifier (UUID or GUID) value.") :arrow_upper_right:

