<!-- loio3c1a297f45ba489283c80d39e97a4218 -->

# UCASE\_syntax Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts all characters in a string to uppercase.



```
UCASE ( <string-expression> )
```



<a name="loio3c1a297f45ba489283c80d39e97a4218__section_gdf_13v_vrb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted to uppercase.



</dd>
</dl>



<a name="loio3c1a297f45ba489283c80d39e97a4218__section_olx_13v_vrb"/>

## Returns

-   LONG NVARCHAR
-   LONG VARCHAR
-   NVARCHAR
-   VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `UCASE` in a `SELECT INTO` statement, you must use `CAST` and set `UCASE` to the correct data type and size.



<a name="loio3c1a297f45ba489283c80d39e97a4218__section_rz4_b3v_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar.
-   SAP database products – `UCASE` is not supported by SAP Adaptive Server Enterprise, but `UPPER` provides the same feature in a compatible manner.



<a name="loio3c1a297f45ba489283c80d39e97a4218__section_snx_b3v_vrb"/>

## Example

The following statement returns the value “CHOCOLATE”:

```
SELECT UCASE( 'ChocoLate' ) FROM iq_dummy
```

**Related Information**  


[UCASE Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a58c382984f2101586a7d1f6dcf499c3.html "Converts all characters in a string to uppercase.") :arrow_upper_right:

