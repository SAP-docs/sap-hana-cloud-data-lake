<!-- loio10843333345b407694db50383c73a083 -->

# UPPER Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Converts all characters in a string to uppercase.



```
UPPER ( <string-expression> );
```



<a name="loio10843333345b407694db50383c73a083__section_it2_tgv_vrb"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be converted to uppercase.



</dd>
</dl>



<a name="loio10843333345b407694db50383c73a083__section_k2p_tgv_vrb"/>

## Result Set

-   LONG NVARCHAR
-   LONG VARCHAR
-   NVARCHAR
-   VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `UPPER` in a `SELECT INTO` statement, you must use `CAST` and set `UPPER` to the correct data type and size.



<a name="loio10843333345b407694db50383c73a083__section_pmh_5gv_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio10843333345b407694db50383c73a083__section_ytv_5gv_vrb"/>

## Example

The following statement returns the value “CHOCOLATE”:

```
SELECT UPPER( 'ChocoLate' ) FROM iq_dummy;
```

**Related Information**  


[UPPER Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a58cbc0284f21015ac14f5baa190b878.html "Converts all characters in a string to uppercase.") :arrow_upper_right:

