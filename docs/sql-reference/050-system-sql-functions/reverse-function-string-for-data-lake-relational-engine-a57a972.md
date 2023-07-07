<!-- loioa57a972e84f2101584c3b9d17a08b0f9 -->

# REVERSE Function \[String\] for Data Lake Relational Engine

Takes one argument as an input of type `BINARY` or `STRING` and returns the specified string with characters listed in reverse order.



```
REVERSE ( <expression> | <uchar_expr> )
```



<a name="loioa57a972e84f2101584c3b9d17a08b0f9__REVERSE_parm1"/>

## Parameters


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

A character or binary-type column name, variable, or constant expression of `CHAR`, `VARCHAR`, `NCHAR`, `NVARCHAR`, `BINARY`, or `VARBINARY` type.



</dd>
</dl>



<a name="loioa57a972e84f2101584c3b9d17a08b0f9__REVERSE_returns1"/>

## Returns

LONG VARCHAR

LONG NVARCHAR

> ### Note:  
> The result data type is a `LONG VARCHAR`. If you use `REVERSE` in a `SELECT INTO` statement, you must use `CAST` and set `REVERSE` to the correct data type and size.



<a name="loioa57a972e84f2101584c3b9d17a08b0f9__REVERSE_remarks1"/>

## Remarks

-   `REVERSE`, a string function, returns the reverse of expression.
-   If expression is NULL, reverse returns NULL.
-   Surrogate pairs are treated as indivisible and are not reversed.



<a name="loioa57a972e84f2101584c3b9d17a08b0f9__REVERSE_standards1"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa57a972e84f2101584c3b9d17a08b0f9__REVERSE_examples1"/>

## Examples

-   The following statement returns the value "dcba":

    ```
    select reverse("abcd")
    ```

-   The following statement returns the value "0x00503412":

    ```
    select reverse(0x12345000)
    ```


**Related Information**  


[LCASE Function \[String\] for Data Lake Relational Engine](lcase-function-string-for-data-lake-relational-engine-a55c82d.md "Converts all characters in a string to lowercase.")

[LEFT Function \[String\] for Data Lake Relational Engine](left-function-string-for-data-lake-relational-engine-a55d883.md "Returns a specified number of characters from the beginning of a string.")

[LOWER Function \[String\] for Data Lake Relational Engine](lower-function-string-for-data-lake-relational-engine-a561324.md "Converts all characters in a string to lowercase.")

[REPLACE Function \[String\] for Data Lake Relational Engine](replace-function-string-for-data-lake-relational-engine-a579952.md "Replaces all occurrences of a substring with another substring.")

[RIGHT Function \[String\] for Data Lake Relational Engine](right-function-string-for-data-lake-relational-engine-a57b364.md "Returns the rightmost characters of a string.")

[UCASE Function \[String\] for Data Lake Relational Engine](ucase-function-string-for-data-lake-relational-engine-a58c382.md "Converts all characters in a string to uppercase.")

[UPPER Function \[String\] for Data Lake Relational Engine](upper-function-string-for-data-lake-relational-engine-a58cbc0.md "Converts all characters in a string to uppercase.")

[String Operators in Data Lake Relational Engine](../010-sql-language-elements/string-operators-in-data-lake-relational-engine-a4f1c6d.md "These string operators are available in data lake Relational Engine.")

[REVERSE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/3310f4b18b7c478f8003d97e82fdbc6a.html "Takes one argument as an input of type BINARY or STRING and returns the specified string with characters listed in reverse order.") :arrow_upper_right:

