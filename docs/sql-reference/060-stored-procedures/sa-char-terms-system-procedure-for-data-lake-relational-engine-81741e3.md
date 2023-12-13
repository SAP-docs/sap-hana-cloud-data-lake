<!-- loio81741e316ce21014a988e4845b1f1a41 -->

# sa\_char\_terms System Procedure for Data Lake Relational Engine

Breaks a CHAR string into terms and returns each term as a row along with its position.



<a name="loio81741e316ce21014a988e4845b1f1a41__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
<text>[, <config_name>[, <owner> ] ] )sa_char_terms(; 
   
```



## Parameters


<dl>
<dt><b>

*<text\>* 

</b></dt>
<dd>

The LONG VARCHAR string you are parsing.



</dd><dt><b>

*<config\_name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the text configuration object to apply when processing the string. The default value is 'default\_char'.



</dd><dt><b>

*<owner\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the owner of the text configuration object. The default value is NULL. The current user is assumed if the owner is not specified or if NULL is specified. The default value is 'SYS'.



</dd>
</dl>



<a name="loio81741e316ce21014a988e4845b1f1a41__section_j2p_3w5_xyb"/>

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

sa\_char\_terms\( The specified term in the *<char-string\>*.

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



## Remarks

Use this system procedure to find out how a string is interpreted when the settings for a text configuration object are applied. This procedure can be helpful when you want to know what terms would be dropped during indexing or from a query string.



<a name="loio81741e316ce21014a988e4845b1f1a41__section_u51_bkf_3jb"/>

## Privilege

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loio81741e316ce21014a988e4845b1f1a41__section_sdp_jnf_zyb"/>

## Examples

This example uses the sa\_char\_terms system procedure to return the terms in the CHAR string "It's a work-at-home day!" using the default CHAR text configuration object, default\_char:

```
CALL sa_char_terms ('It''s a work-at-home day!', 'default_char', 'sys');
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

