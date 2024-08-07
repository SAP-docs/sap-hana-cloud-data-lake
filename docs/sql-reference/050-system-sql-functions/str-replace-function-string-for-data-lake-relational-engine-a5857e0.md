<!-- loioa5857e0a84f210158b54cac40679f568 -->

# STR\_REPLACE Function \[String\] for Data Lake Relational Engine

Takes three arguments as input of type `BINARY` or `STRING` and replaces any instances of the second string expression \(*<string\_expr2\>*\) that occur within the first string expression \(*<string\_expr1\>*\) with a third expression \(*<string\_expr3\>*\).



```
REPLACE ( <string_expr1>, <string_expr2>, <string_expr3> );
```



<a name="loioa5857e0a84f210158b54cac40679f568__STR_REPLACE_parm1"/>

## Parameters


<dl>
<dt><b>

*<string\_expr1\>*

</b></dt>
<dd>

The source string, or the string expression to be searched, expressed as VARCHAR, VARBINARY, or BINARY data type.



</dd><dt><b>

*<string\_expr2\>*

</b></dt>
<dd>

The pattern string, or the string expression to find within the first expression \(*<string\_expr1\>*\) and is expressed as VARCHAR, VARBINARY, or BINARY data type.



</dd><dt><b>

*<string\_expr3\>*

</b></dt>
<dd>

The replacement string expression, expressed as VARCHAR, VARBINARY, or BINARY data type.



</dd>
</dl>



<a name="loioa5857e0a84f210158b54cac40679f568__STR_REPLACE_remarks1"/>

## Remarks

`STR_REPLACE` is an alias of `REPLACE` function.

-   Takes any data type as input and returns STRING or BINARY.

    For example, an empty string passed as an argument \(`""`\) is replaced with one space \(`" "`\) before further evaluation occurs. This is true for both `BINARY` and `STRING` types.

-   All arguments can have a combination of `BINARY` and `STRING` data types.

-   The result length may vary, depending upon what is known about the argument values when the expression is compiled. If all arguments are columns or host variables assigned to constants, data lake Relational Engine calculates the result length as:

    ```
    result_length = ((s/p)*(r-p)+s)
    WHERE
      s = length of source string
      p = length of pattern string
      r = length of replacement string
    IF (r-p) <= 0, result length = s;
    ```

-   If data lake Relational Engine cannot calculate the result length because the argument values are unknown when the expression is compiled, the result length used is 255.

-   `RESULT_LEN` never exceeds 32767.




<a name="loioa5857e0a84f210158b54cac40679f568__STR_REPLACE_standards1"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loioa5857e0a84f210158b54cac40679f568__STR_REPLACE_example1"/>

## Examples

-   Replaces the string *<def\>* within the string *<cdefghi\>* with *<yyy\>*:

    ```
    select replace("cdefghi", "def", "yyy");
    -------------
    cyyyghi
    (1 row(s) affected)
    ```

-   Replaces all spaces with “toyota”:

    ```
    select str_replace ("chevy, ford, mercedes", "","toyota");
    ----------
    chevy,toyotaford,toyotamercedes
    (1 row(s) affected)
    ```

-   Accepts NULL in the third parameter and treats it as an attempt to replace *<string\_expr2\>* with NULL, effectively turning STR\_REPLACE into a “string cut” operation. Returns “abcghijklm”:

    ```
    select str_replace("abcdefghijklm", "def", NULL);
    ----------
    abcghijklm
    (1 row affected)
    ```


**Related Information**  


[String Functions in Data Lake Relational Engine](string-functions-in-data-lake-relational-engine-a52d1d9.md "String functions perform conversion, extraction, or manipulation operations on strings, or return information about strings.")

[STR_REPLACE Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/d0e04740ba8f44cfb34a48fe3c6e06ae.html "Takes three arguments as input of type BINARY or STRING and replaces any instances of the second string expression (string_expr2) that occur within the first string expression (string_expr1) with a third expression (string_expr3).") :arrow_upper_right:

