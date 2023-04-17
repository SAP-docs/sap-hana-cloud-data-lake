<!-- loio554cede3499a4ef98a05be128493031f -->

# ASCII Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the integer ASCII value of the first byte in a *<string-expression\>*.



```
ASCII ( <string-expression> )
```



<a name="loio554cede3499a4ef98a05be128493031f__section_hml_tjk_srb"/>

## Parameters

 *<string-expression\>*
 :   The string.

 

<a name="loio554cede3499a4ef98a05be128493031f__section_nyd_5jk_srb"/>

## Returns

SMALLINT



<a name="loio554cede3499a4ef98a05be128493031f__section_fly_5jk_srb"/>

## Remarks

If the string is empty, `ASCII` returns zero. Literal strings must be enclosed in quotes.



<a name="loio554cede3499a4ef98a05be128493031f__section_f5t_vjk_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loio554cede3499a4ef98a05be128493031f__section_bf5_wjk_srb"/>

## Example

The following statement returns the value 90, when the collation sequence is set to the default ISO\_BINENG:

```
SELECT ASCII( 'Z' ) FROM iq_dummy
```

**Related Information**  


[ASCII Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a533e3a684f21015a2a0af73e4a9ad1c.html "Returns the integer ASCII value of the first byte in a string-expression.") :arrow_upper_right:

