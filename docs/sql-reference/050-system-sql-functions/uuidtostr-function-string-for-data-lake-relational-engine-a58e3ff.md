<!-- loioa58e3ffd84f2101593c5c09c7d64fec4 -->

# UUIDTOSTR Function \[String\] for Data Lake Relational Engine

Converts a unique identifier value \(UUID, also known as GUID\) to a string value.



```
UUIDTOSTR ( <uuid-expression> );
```



<a name="loioa58e3ffd84f2101593c5c09c7d64fec4__UUIDTOSTR_parm1"/>

## Parameters


<dl>
<dt><b>

*<uuid-expression\>*

</b></dt>
<dd>

A unique identifier value.



</dd>
</dl>



<a name="loioa58e3ffd84f2101593c5c09c7d64fec4__UUIDTOSTR_returns1"/>

## Result Set

VARCHAR



<a name="loioa58e3ffd84f2101593c5c09c7d64fec4__UUIDTOSTR_remarks1"/>

## Remarks

Converts a unique identifier to a string value in the format *<xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx\>*, where x is a hexadecimal digit. If the binary value is not a valid unique identifier, NULL is returned.



<a name="loioa58e3ffd84f2101593c5c09c7d64fec4__UUIDTOSTR_standards1"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa58e3ffd84f2101593c5c09c7d64fec4__UUIDTOSTR_example1"/>

## Examples

To convert a unique identifier value into a readable format, execute a query similar to:

```
CREATE TABLE T3 (
pk uniqueidentifier primary key,c1 int);
INSERT INTO T3 (pk, c1) 
values (0x12345678123456789012123456789012, 1)
SELECT UUIDTOSTR(pk) FROM T3;
```

**Related Information**  


[UUIDTOSTR Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/60f4cba865204365bd10f0d9cfb44fc6.html "Converts a unique identifier value (UUID, also known as GUID) to a string value.") :arrow_upper_right:

