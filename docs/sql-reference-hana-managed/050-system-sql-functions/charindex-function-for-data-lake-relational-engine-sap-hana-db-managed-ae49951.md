<!-- loioae499513aa0346978ca7d3c6f34656da -->

# CHARINDEX Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the position of the first occurrence of a specified string in another string.



```
CHARINDEX ( <string-expression1>, <string-expression2> );
```



<a name="loioae499513aa0346978ca7d3c6f34656da__section_gjm_fsl_srb"/>

## Parameters


<dl>
<dt><b>

*<string-expression1\>*

</b></dt>
<dd>

The string for which you are searching. This string is limited to 255 bytes.



</dd><dt><b>

*<string-expression2\>*

</b></dt>
<dd>

The string to be searched. The position of the first character in the string being searched is 1.



</dd>
</dl>



<a name="loioae499513aa0346978ca7d3c6f34656da__section_cdy_fsl_srb"/>

## Result Set

INT



<a name="loioae499513aa0346978ca7d3c6f34656da__section_rkp_gsl_srb"/>

## Remarks

All the positions or offsets, returned or specified, in the `CHARINDEX` function are always character offsets and may be different from the byte offset for multibyte data.

If the string being searched:

-   Contains more than one instance of the specified string, CHARINDEX returns the position of the first instance.
-   Does not contain the specified string, CHARINDEX returns zero \(0\).

Searching for a zero-length string returns 1.

If any of the arguments is NULL, the result is NULL.

CHARINDEX returns a 32 bit signed integer position for CHAR and VARCHAR columns.



<a name="loioae499513aa0346978ca7d3c6f34656da__section_r5k_hsl_srb"/>

## Standards and Compatibility

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioae499513aa0346978ca7d3c6f34656da__section_k1c_3sl_srb"/>

## Examples

This example uses the following statement:

```
SELECT Surname, GivenName
FROM Employees
WHERE CHARINDEX('K', Surname ) = 1;
```

The statement returns the following values:


<table>
<tr>
<th valign="top" rowspan="1">

Surname

</th>
<th valign="top" rowspan="1">

GivenName

</th>
</tr>
<tr>
<td valign="top" rowspan="1">

Klobucher

</td>
<td valign="top" rowspan="1">

James

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Kuo

</td>
<td valign="top" rowspan="1">

Felicia

</td>
</tr>
<tr>
<td valign="top" rowspan="1">

Kelly

</td>
<td valign="top" rowspan="1">

Moira

</td>
</tr>
</table>

**Related Information**  


[CHARINDEX Function \[String\] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a53cde2984f210158cbd968731b1879c.html "Returns the position of the first occurrence of a specified string in another string.") :arrow_upper_right:

