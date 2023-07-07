<!-- loio76ddacf92fe949c3a5deee67aae74a46 -->

# HTML\_DECODE Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Decodes special character entities that appear in HTML literal strings.



```
HTML_DECODE( <string> )
```



<a name="loio76ddacf92fe949c3a5deee67aae74a46__section_rh2_5ng_trb"/>

## Parameters


<dl>
<dt><b>

 *<string\>* 

</b></dt>
<dd>

Arbitrary literal string used in an HTML document.



</dd>
</dl>



<a name="loio76ddacf92fe949c3a5deee67aae74a46__section_qsq_5ng_trb"/>

## Returns

LONG VARCHAR or LONG NVARCHAR.

> ### Note:  
> The result data type is a LONG VARCHAR. If you use HTML\_DECODE in a SELECT INTO statement, you need a Unstructured Data Analytics Option license or to use CAST and set HTML\_DECODE to the correct data type and size.



<a name="loio76ddacf92fe949c3a5deee67aae74a46__section_xbk_vng_trb"/>

## Remarks

This function returns the string argument after making the appropriate substitutions. The following table contains a sampling of the acceptable character entities.


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

&quot;



</td>
<td valign="top">

"



</td>
</tr>
<tr>
<td valign="top">

&\#39;



</td>
<td valign="top">

'



</td>
</tr>
<tr>
<td valign="top">

&amp;



</td>
<td valign="top">

&



</td>
</tr>
<tr>
<td valign="top">

&lt;



</td>
<td valign="top">

<



</td>
</tr>
<tr>
<td valign="top">

&gt;



</td>
<td valign="top">

\>



</td>
</tr>
<tr>
<td valign="top">

&\#x*<hexadecimal-number\>*;



</td>
<td valign="top">

Unicode codepoint, specified as a hexadecimal number. For example, &\#x27; returns a single apostrophe.



</td>
</tr>
<tr>
<td valign="top">

&\#*<decimal-number\>*;



</td>
<td valign="top">

Unicode codepoint, specified as a decimal number. For example, &\#8482; returns the trademark symbol.



</td>
</tr>
</table>

When a Unicode codepoint is specified, if the value can be converted to a character in the database character set, it is converted to a character. Otherwise, it is returned uninterpreted.

 Data lake Relational Engine supports all character entity references specified in the HTML 4.01 Specification.



<a name="loio76ddacf92fe949c3a5deee67aae74a46__section_nvw_vng_trb"/>

## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following statement returns the string `<p>The piano was made by 'Steinway & Sons'.</p>`:

```
SELECT HTML_DECODE('&lt;p&gt;The piano was made ' ||
  'by &lsquo;Steinway &amp; Sons&rsquo;.&lt;/p&gt;');
```

The following statement returns the string `<p>It cost €85.000,000.</p>`:

```
SELECT HTML_DECODE('&lt;p&gt;It cost &euro;85.000,000.&lt;/p&gt;');
```

**Related Information**  


[HTML_DECODE Function [Miscellaneous] for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/81f8bbdd6ce21014a76ca7e38126b096.html "Decodes special character entities that appear in HTML literal strings.") :arrow_upper_right:

