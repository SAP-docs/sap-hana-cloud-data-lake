<!-- loio3be6b7a46c5f1014b420d21c4b0f3634 -->

# SYSARTICLE System View for Data Lake Relational Engine

Each row of the SYSARTICLE system view describes an article in a publication. The underlying system table for this view is ISYSARTICLE.



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

publication\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The publication of which the article is a part.



</td>
</tr>
<tr>
<td valign="top">

table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

Each article consists of columns and rows from a single table. This column contains the table ID for this table.



</td>
</tr>
<tr>
<td valign="top">

where\_expr



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

For articles that contain a subset of rows defined by a WHERE clause, this column contains the search condition.



</td>
</tr>
<tr>
<td valign="top">

subscribe\_by\_expr



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

For articles that contain a subset of rows defined by a SUBSCRIBE BY expression, this column contains the expression.



</td>
</tr>
<tr>
<td valign="top">

query



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates information about the article type to the database server.



</td>
</tr>
<tr>
<td valign="top">

alias



</td>
<td valign="top">

VARCHAR\(256\)



</td>
<td valign="top">

The alias for the article.



</td>
</tr>
<tr>
<td valign="top">

schema\_change\_active



</td>
<td valign="top">

BIT



</td>
<td valign="top">

1 if the table and publication are part of a synchronization schema change.



</td>
</tr>
</table>

**Related Information**  


[SYSARTICLECOL System View for Data Lake Relational Engine](sysarticlecol-system-view-for-data-lake-relational-engine-3be6c15.md "Each row of the SYSARTICLECOL system view identifies a column in an article. The underlying system table for this view is ISYSARTICLECOL.")

[SYSARTICLECOLS Consolidated View for Data Lake Relational Engine](sysarticlecols-consolidated-view-for-data-lake-relational-engine-3be6ca2.md "Each row in the SYSARTICLECOLS view identifies a column in an article.")

