<!-- loio81741e316ce21014a988e4845b1f1a41 -->

# sa\_char\_terms System Procedure for Data Lake Relational Engine

Breaks a CHAR string into terms and returns each term as a row along with its position.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_char_terms( 
<text>
[, <config_name>
[, <owner> ] ] 
)
```



## Parameters

 *<text\>* 
:   The LONG VARCHAR string you are parsing.

  *<config\_name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the text configuration object to apply when processing the string. The default value is 'default\_char'.

   *<owner\>* 
 :   Use this optional CHAR\(128\) parameter to specify the owner of the text configuration object. The default value is NULL. The current user is assumed if the owner is not specified or if NULL is specified.

 

## Remarks

Use this system procedure to find out how a string is interpreted when the settings for a text configuration object are applied. This procedure can be helpful when you want to know what terms would be dropped during indexing or from a query string.



<a name="loio81741e316ce21014a988e4845b1f1a41__section_u51_bkf_3jb"/>

## Permissions

You need to have the EXECUTE privilege on the system procedure.



## Side Effects

None



The following statement returns the terms in the CHAR string "It's a work-at-home day!" using the default CHAR text configuration object, default\_char:

```
CALL dbo.sa_char_terms ('It's a work-at-home day!', 'default_char', 'sys');
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

