<!-- loiod0e04740ba8f44cfb34a48fe3c6e06ae -->

# STR\_REPLACE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Takes three arguments as input of type `BINARY` or `STRING` and replaces any instances of the second string expression \(*<string\_expr2\>*\) that occur within the first string expression \(*<string\_expr1\>*\) with a third expression \(*<string\_expr3\>*\).



```
REPLACE ( <string_expr1>, <string_expr2>, <string_expr3> );
```



<a name="loiod0e04740ba8f44cfb34a48fe3c6e06ae__section_sx3_nt5_vrb"/>

## Parameters


<dl>
<dt><b>

*<string\_expr1\>*

</b></dt>
<dd>

The source string, or the string expression to be searched, expressed as VARCHAR, UNICHAR, UNIVARCHAR,VARBINARY, or BINARY data type.



</dd><dt><b>

*<string\_expr2\>*

</b></dt>
<dd>

The pattern string, or the string expression to find within the first expression \(*<string\_expr1\>*\) and is expressed as VARCHAR, UNICHAR, UNIVARCHAR,VARBINARY, or BINARY data type.



</dd><dt><b>

*<string\_expr3\>*

</b></dt>
<dd>

The replacement string expression, expressed as VARCHAR, UNICHAR, UNIVARCHAR,VARBINARY, or BINARY data type.



</dd>
</dl>



<a name="loiod0e04740ba8f44cfb34a48fe3c6e06ae__section_opj_4t5_vrb"/>

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




<a name="loiod0e04740ba8f44cfb34a48fe3c6e06ae__section_ndz_4t5_vrb"/>

## Standards and Compatibility

SQL – Transact-SQL extension to ISO/ANSI SQL grammar



<a name="loiod0e04740ba8f44cfb34a48fe3c6e06ae__section_tv3_pt5_vrb"/>

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


[STR_REPLACE Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/a5857e0a84f210158b54cac40679f568.html "Takes three arguments as input of type BINARY or STRING and replaces any instances of the second string expression (string_expr2) that occur within the first string expression (string_expr1) with a third expression (string_expr3).") :arrow_upper_right:

