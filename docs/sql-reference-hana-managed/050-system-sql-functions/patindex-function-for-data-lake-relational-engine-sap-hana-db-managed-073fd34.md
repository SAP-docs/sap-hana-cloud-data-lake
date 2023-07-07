<!-- loio073fd346f10a409b98efefed3192ff77 -->

# PATINDEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the starting position of the first occurrence of a specified pattern.



```
PATINDEX ( '%<pattern>%', <string-expression> )
```



<a name="loio073fd346f10a409b98efefed3192ff77__section_vnz_vln_vrb"/>

## Parameters


<dl>
<dt><b>

*<pattern\>*

</b></dt>
<dd>

The pattern for which you are searching. This string is limited to 126 bytes for patterns with wildcards. If the leading percent wildcard is omitted, `PATINDEX` returns one \(1\) if the pattern occurs at the beginning of the string, and zero if not. If *<pattern\>* starts with a percent wildcard, then the two leading percent wildcards are treated as one.

Patterns without wildcards \(percent % or underscore \_\) can be up to 255 bytes in length.



</dd><dt><b>

*<string-expression\>*

</b></dt>
<dd>

The string to be searched for the pattern.



</dd>
</dl>



<a name="loio073fd346f10a409b98efefed3192ff77__section_vqs_wln_vrb"/>

## Returns

INT



<a name="loio073fd346f10a409b98efefed3192ff77__section_y4c_xln_vrb"/>

## Remarks

`PATINDEX` returns the starting position of the first occurrence of the pattern. If the string being searched contains more than one instance of the string pattern, `PATINDEX` returns only the position of the first instance.

The pattern uses the same wildcards as the `LIKE` comparison. This table lists the pattern wildcards:


<table>
<tr>
<th valign="top">

Wildcard



</th>
<th valign="top">

Matches



</th>
</tr>
<tr>
<td valign="top">

\_ \(underscore\)



</td>
<td valign="top">

Any one character



</td>
</tr>
<tr>
<td valign="top">

% \(percent\)



</td>
<td valign="top">

Any string of zero or more characters



</td>
</tr>
<tr>
<td valign="top">

\[\]



</td>
<td valign="top">

Any single character in the specified range or set



</td>
</tr>
<tr>
<td valign="top">

\[^\]



</td>
<td valign="top">

Any single character not in the specified range or set



</td>
</tr>
</table>

If the pattern is not found, `PATINDEX` returns zero \(0\).

Searching for a pattern longer than 126 bytes returns NULL.

Searching for a zero-length string returns 1.

If any of the arguments is NULL, the result is zero \(0\).

All the positions or offsets, returned or specified, in the `PATINDEX` function are always character offsets and may be different from the byte offset for multibyte data.

`PATINDEX` returns a 32-bit unsigned integer position for `CHAR` and `VARCHAR` columns.



<a name="loio073fd346f10a409b98efefed3192ff77__section_wxn_yln_vrb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – compatible with SAP Adaptive Server Enterprise



<a name="loio073fd346f10a409b98efefed3192ff77__section_xhx_yln_vrb"/>

## Examples

-   The following statement returns the value 2:

    ```
    SELECT PATINDEX( '%hoco%', 'chocolate' ) FROM iq_dummy
    ```

-   The following statement returns the value 11:

    ```
    SELECT PATINDEX ('%4_5_', '0a1A 2a3A 4a5A') FROM iq_dummy
    ```


**Related Information**  


[PATINDEX Function [String] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a56c8f8684f210158653d0c858b0e559.html "Returns the starting position of the first occurrence of a specified pattern.") :arrow_upper_right:

