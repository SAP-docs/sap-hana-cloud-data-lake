<!-- loioa58683c184f21015bb5cb68f114bbcb9 -->

# STRTOUUID Function \[String\] for Data Lake Relational Engine

Converts a string value to a unique identifier \(UUID or GUID\) value.



```
STRTOUUID ( <string-expression> ); 
```



<a name="loioa58683c184f21015bb5cb68f114bbcb9__STRTOUUID_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>* 

</b></dt>
<dd>

A string in the format *<xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\>*



</dd>
</dl>



<a name="loioa58683c184f21015bb5cb68f114bbcb9__STRTOUUID_returns1"/>

## Result Set

UNIQUEIDENTIFIER



<a name="loioa58683c184f21015bb5cb68f114bbcb9__STRTOUUID_remarks1"/>

## Remarks

Converts a string in the format *<xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\>* where *<x\>* is a hexadecimal digit, to a unique identifier value. If the string is not a valid UUID string, NULL is returned.

You can use `STRTOUUID` to insert UUID values into a data lake Relational Engine database.



<a name="loioa58683c184f21015bb5cb68f114bbcb9__STRTOUUID_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58683c184f21015bb5cb68f114bbcb9__STRTOUUID_example1"/>

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


[STRTOUUID Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/5572345aa04d4c2fbd9b9589ed18e296.html "Converts a string value to a unique identifier (UUID or GUID) value.") :arrow_upper_right:

