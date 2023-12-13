<!-- loioa586010d84f210158657b25cdb264bf0 -->

# STRING Function \[String\] for Data Lake Relational Engine

Concatenates one or more strings into one large string.



```
STRING ( <string-expression> [ , … ] );
```



<a name="loioa586010d84f210158657b25cdb264bf0__STRING_parm1"/>

## Parameters


<dl>
<dt><b>

*<string-expression\>*

</b></dt>
<dd>

A string. If only one argument is supplied, it is converted into a single expression. If more than one argument is supplied, they are concatenated into a single string. A NULL is treated as an empty string \(''\).



</dd>
</dl>



<a name="loioa586010d84f210158657b25cdb264bf0__STRING_returns1"/>

## Result Set

-   LONG BINARY
-   LONG NVARCHAR
-   LONG VARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `STRING` in a `SELECT INTO` statement, you must use `CAST` and set `STRING` to the correct data type and size.



<a name="loioa586010d84f210158657b25cdb264bf0__STRING_remarks1"/>

## Remarks

Numeric or date parameters are converted to strings before concatenation. You can also use the `STRING` function to convert any single expression to a string by supplying that expression as the only parameter.

If all parameters are NULL, `STRING` returns NULL.



<a name="loioa586010d84f210158657b25cdb264bf0__STRING_standards1"/>

## Standards and Compatibility

-   SQL – Transact-SQL extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa586010d84f210158657b25cdb264bf0__STRING_example1"/>

## Example

The following statement returns the value testing123:

```
SELECT STRING( 'testing', NULL, 123 )
FROM iq_dummy;
```

**Related Information**  


[STRING Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/4b6311065965472286c536537d380f53.html "Concatenates one or more strings into one large string.") :arrow_upper_right:

