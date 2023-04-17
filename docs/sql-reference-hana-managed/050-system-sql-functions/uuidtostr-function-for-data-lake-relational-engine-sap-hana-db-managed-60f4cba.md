<!-- loio60f4cba865204365bd10f0d9cfb44fc6 -->

# UUIDTOSTR Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts a unique identifier value \(UUID, also known as GUID\) to a string value.



```
UUIDTOSTR ( <uuid-expression> )
```



<a name="loio60f4cba865204365bd10f0d9cfb44fc6__section_lmc_jgv_vrb"/>

## Parameters

 *<uuid-expression\>*
 :   A unique identifier value.

 

<a name="loio60f4cba865204365bd10f0d9cfb44fc6__section_td4_jgv_vrb"/>

## Returns

VARCHAR



<a name="loio60f4cba865204365bd10f0d9cfb44fc6__section_mvy_jgv_vrb"/>

## Remarks

Converts a unique identifier to a string value in the format *<xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\>*, where x is a hexadecimal digit. If the binary value is not a valid unique identifier, NULL is returned.



<a name="loio60f4cba865204365bd10f0d9cfb44fc6__section_l2z_kgv_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loio60f4cba865204365bd10f0d9cfb44fc6__section_wsh_lgv_vrb"/>

## Example

To convert a unique identifier value into a readable format, execute a query similar to:

```
CREATE TABLE T3 (
pk uniqueidentifier primary key,c1 int);
INSERT INTO T3 (pk, c1) 
values (0x12345678123456789012123456789012, 1)
SELECT UUIDTOSTR(pk) FROM T3
```

**Related Information**  


[UUIDTOSTR Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58e3ffd84f2101593c5c09c7d64fec4.html "Converts a unique identifier value (UUID, also known as GUID) to a string value.") :arrow_upper_right:

