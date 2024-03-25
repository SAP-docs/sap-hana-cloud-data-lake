<!-- loioa5fba8a784f21015abe39fe3a6d391ea -->

# sa\_nchar\_terms System Procedure for Data Lake Relational Engine

Breaks an `NCHAR` string into terms and returns each term as a row along with its position.



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_nchar_terms
   ( '<char-string>' [ , '<text-config-name>' [, '<owner>' ] ] ] )
```



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_91"/>

## Parameters


<dl>
<dt><b>

*<char-string\>*

</b></dt>
<dd>

The `NCHAR` string you are parsing.



</dd><dt><b>

*<text-config-name\>*

</b></dt>
<dd>

\(Optional\) The text configuration object to apply when processing the string. The default value is '`default_nchar`'.



</dd><dt><b>

*<owner\>*

</b></dt>
<dd>

\(Optional\) The owner of the specified text configuration object. The default value is SYS.



</dd>
</dl>



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__section_j2p_3w5_xyb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Term

</td>
<td valign="top">

The specified term in the *<char-string\>*.

</td>
</tr>
<tr>
<td valign="top">

Position

</td>
<td valign="top">

The position of the term in the *<char-string\>*.

</td>
</tr>
</table>



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_92"/>

## Remarks

You can use `sa_nchar_terms` to find out how a string is interpreted when the settings for a text configuration object are applied. This can be helpful when you want to know what terms would be dropped during indexing or from a query string.

The syntax for `sa_nchar_terms` is similar to the syntax for the `sa_char_terms` system procedure.

> ### Note:  
> The `NCHAR` data type is supported only for `IN SYSTEM` tables.



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__iq_iquda_93"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__section_sfr_3ss_mbb"/>

## Side Effects

None



<a name="loioa5fba8a784f21015abe39fe3a6d391ea__section_y3p_4x5_xyb"/>

## Examples

This example uses the sa\_nchar\_terms system procedure to return the terms in the NCHAR string "It's a work-at-home day!" using the default CHAR text configuration object, default\_char:

```
CALL sa_nchar_terms ('It''s a work-at-home day!', 'default_char', 'sys');
```


<table>
<tr>
<th valign="top">

term

</th>
<th valign="top">

position

</th>
</tr>
<tr>
<td valign="top">

It

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

s

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

work

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

at

</td>
<td valign="top">

5

</td>
</tr>
<tr>
<td valign="top">

home

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

day

</td>
<td valign="top">

7

</td>
</tr>
</table>

