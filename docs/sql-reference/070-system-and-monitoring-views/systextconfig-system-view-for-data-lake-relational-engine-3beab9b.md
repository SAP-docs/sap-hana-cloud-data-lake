<!-- loio3beab9b86c5f1014a866ef25010196f0 -->

# SYSTEXTCONFIG System View for Data Lake Relational Engine

Each row in the SYS.SYSTEXTCONFIG system view describes one text configuration object, for use with the full text search feature.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID for the text configuration object.



</td>
</tr>
<tr>
<td valign="top">

creator



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The creator of the text configuration object.



</td>
</tr>
<tr>
<td valign="top">

term\_breaker



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The algorithm used to separate a string into terms or words. Values are 0 for GENERIC and 1 for NGRAM. With GENERIC, any string of one or more alphanumeric characters separated by nonalphanumerics are treated as a term. NGRAM is for approximate matching or for documents that don’t use a whitespace to separate terms.



</td>
</tr>
<tr>
<td valign="top">

stemmer



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

min\_term\_length



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The minimum length, in characters, allowed for a term. Terms that are shorter than min\_term\_length are ignored.

The MINIMUM TERM LENGTH setting is only meaningful for the GENERIC term breaker. For NGRAM text indexes, the setting is ignored.



</td>
</tr>
<tr>
<td valign="top">

max\_term\_length



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

For GENERIC text indexes, the maximum length, in characters, allowed for a term. Terms that are longer than max\_term\_length are ignored.

For NGRAM text indexes, this is the length of the n-grams into which terms are broken.



</td>
</tr>
<tr>
<td valign="top">

collation



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

text\_config\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the text configuration object.



</td>
</tr>
<tr>
<td valign="top">

prefilter



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The function and library name for an external prefilter library.



</td>
</tr>
<tr>
<td valign="top">

postfilter



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

char\_stoplist



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Terms to ignore when performing a full text search on CHAR columns. These terms are also omitted from text indexes. This column is used when the text configuration object is created from default\_char.



</td>
</tr>
<tr>
<td valign="top">

nchar\_stoplist



</td>
<td valign="top">

LONG NVARCHAR



</td>
<td valign="top">

Terms to ignore when performing a full text search on NCHAR columns. These terms are also omitted from text indexes. This column is used when the text configuration object is created from default\_nchar.



</td>
</tr>
<tr>
<td valign="top">

external\_term\_breaker



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The function and library name for an external term breaker library.



</td>
</tr>
</table>

