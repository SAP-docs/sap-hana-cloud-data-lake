<!-- loio93a8ffefb9d74ce5a0354d391cafc925 -->

# HTML\_ENCODE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Encodes special characters within strings to be inserted into HTML documents.



```
HTML_ENCODE( <string> )
```



<a name="loio93a8ffefb9d74ce5a0354d391cafc925__section_cg5_pmg_trb"/>

## Parameters

  *<string\>* 
 :   Arbitrary string to be used in an HTML document.

 

<a name="loio93a8ffefb9d74ce5a0354d391cafc925__section_lrh_qmg_trb"/>

## Returns

LONG VARCHAR or LONG NVARCHAR.

> ### Note:  
> The result data type is a LONG VARCHAR. If you use HTML\_ENCODE in a SELECT INTO statement, you need a Unstructured Data Analytics Option license or to use CAST and set HTML\_DECODE to the correct data type and size.



<a name="loio93a8ffefb9d74ce5a0354d391cafc925__section_uj4_rmg_trb"/>

## Remarks

This function returns the string argument after making the following set of substitutions:


<table>
<tr>
<th valign="top">

Characters



</th>
<th valign="top">

Substitution



</th>
</tr>
<tr>
<td valign="top">

"



</td>
<td valign="top">

&quot;



</td>
</tr>
<tr>
<td valign="top">

'



</td>
<td valign="top">

&\#39;



</td>
</tr>
<tr>
<td valign="top">

&



</td>
<td valign="top">

&amp;



</td>
</tr>
<tr>
<td valign="top">

<



</td>
<td valign="top">

&lt;



</td>
</tr>
<tr>
<td valign="top">

\>



</td>
<td valign="top">

&gt;



</td>
</tr>
<tr>
<td valign="top">

codes *<nn\>* less than 0x20



</td>
<td valign="top">

&\#x*<nn\>*;



</td>
</tr>
</table>

This function supports NCHAR inputs and/or outputs.



<a name="loio93a8ffefb9d74ce5a0354d391cafc925__section_k4t_lm3_wrb"/>

## Standards and Compatibility

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

The following example returns the string `'&lt;!DOCTYPE HTML PUBLIC &quot;-//W3C//DTD HTML 4.01//EN&quot;&gt; '`.

```
SELECT HTML_ENCODE('<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">');
```

**Related Information**  


[HTML_ENCODE Function [Miscellaneous] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/81f8c4b16ce21014aa14a17df2f5d8b1.html "Encodes special characters within strings to be inserted into HTML documents.") :arrow_upper_right:

