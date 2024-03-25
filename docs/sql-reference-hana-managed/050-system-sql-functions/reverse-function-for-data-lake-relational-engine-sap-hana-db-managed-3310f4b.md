<!-- loio3310f4b18b7c478f8003d97e82fdbc6a -->

# REVERSE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Takes one argument as an input of type `BINARY` or `STRING` and returns the specified string with characters listed in reverse order.



```
REVERSE ( <expression> | <uchar_expr> );
```



<a name="loio3310f4b18b7c478f8003d97e82fdbc6a__section_fnt_wn3_wrb"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

A character or binary-type column name, variable, or constant expression of `CHAR`, `VARCHAR`, `NCHAR`, `NVARCHAR`, `BINARY`, or `VARBINARY` type.



</dd>
</dl>



<a name="loio3310f4b18b7c478f8003d97e82fdbc6a__section_stt_xn3_wrb"/>

## Result Set

LONG VARCHAR

LONG NVARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REVERSE` in a `SELECT INTO` statement, you must use `CAST` and set `REVERSE` to the correct data type and size.



<a name="loio3310f4b18b7c478f8003d97e82fdbc6a__section_p2b_kc5_vrb"/>

## Remarks

-   `REVERSE`, a string function, returns the reverse of expression.
-   If expression is NULL, reverse returns NULL.
-   Surrogate pairs are treated as indivisible and are not reversed.



<a name="loio3310f4b18b7c478f8003d97e82fdbc6a__section_jyx_yn3_wrb"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loio3310f4b18b7c478f8003d97e82fdbc6a__section_vfx_zn3_wrb"/>

## Examples

-   The following statement returns the value "dcba":

    ```
    select reverse("abcd");
    ```

-   The following statement returns the value "0x00503412":

    ```
    select reverse(0x12345000);
    ```


**Related Information**  


[REVERSE Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/a57a972e84f2101584c3b9d17a08b0f9.html "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.") :arrow_upper_right:

