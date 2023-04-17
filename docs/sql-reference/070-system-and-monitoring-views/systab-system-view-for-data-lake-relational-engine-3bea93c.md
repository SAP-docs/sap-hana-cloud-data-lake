<!-- loio3bea93c06c5f1014a83df5f526a8a9d2 -->

# SYSTAB System View for Data Lake Relational Engine

Each row of the SYSTAB system view describes one table or view in the database. Additional information for views can be found in the SYSVIEW system view. The underlying system table for this view is ISYSTAB.



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

table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

Each table is assigned a unique number \(the table number\).



</td>
</tr>
<tr>
<td valign="top">

dbspace\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

A value indicating which dbspace contains the table.



</td>
</tr>
<tr>
<td valign="top">

count



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The number of rows in the table or materialized view. This value is updated during each successful checkpoint. This number is used to optimize database access. The count is always 0 for a non-materialized view or remote table.



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

The user number of the owner of the table or view.



</td>
</tr>
<tr>
<td valign="top">

table\_page\_count



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The total number of main pages used by the underlying table.



</td>
</tr>
<tr>
<td valign="top">

ext\_page\_count



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The total number of extension pages used by the underlying table.



</td>
</tr>
<tr>
<td valign="top">

commit\_action



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

For global temporary tables, 0 indicates that the ON COMMIT PRESERVE ROWS clause was specified when the table was created, 1 indicates that the ON COMMIT DELETE ROWS clause was specified when the table was created \(the default behavior for temporary tables\), and 3 indicates that the NOT TRANSACTIONAL clause was specified when the table was created. For non-temporary tables, commit\_action is always 0.



</td>
</tr>
<tr>
<td valign="top">

share\_type



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

For global temporary tables, 4 indicates that the SHARE BY ALL clause was specified when the table was created, and 5 indicates that the SHARE BY ALL clause was *not* specified when the table was created. For non-temporary tables, share\_type is always 5 because the SHARE BY ALL clause cannot be specified when creating non-temporary tables.



</td>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the table.



</td>
</tr>
<tr>
<td valign="top">

last\_modified\_at



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The local time at which the data in the table was last modified. This column is only updated at checkpoint time.



</td>
</tr>
<tr>
<td valign="top">

table\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the table or view. One creator cannot have two tables or views with the same name.



</td>
</tr>
<tr>
<td valign="top">

table\_type



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The type of table or view. Values include:

 1
 :   Base table

  2
 :   Materialized view

  3
 :   Global temporary table

  4
 :   Local temporary table

  5
 :   Text index base table

  6
 :   Text index global temporary table

  7
 :   Table partition

  21
 :   View

 

</td>
</tr>
<tr>
<td valign="top">

replicate



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

This value is for internal use only.



</td>
</tr>
<tr>
<td valign="top">

server\_type



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The location of the data for the underlying table. Values include:

 1
 :   Local server

  2
 :   IQ table

  3
 :   Remote server

 

</td>
</tr>
<tr>
<td valign="top">

tab\_page\_list



</td>
<td valign="top">

LONG VARBIT



</td>
<td valign="top">

For internal use only. The set of pages that contain information for the table, expressed as a bitmap.



</td>
</tr>
<tr>
<td valign="top">

ext\_page\_list



</td>
<td valign="top">

LONG VARBIT



</td>
<td valign="top">

For internal use only. The set of pages that contain row extensions and large object \(LOB\) pages for the table, expressed as a bitmap.



</td>
</tr>
<tr>
<td valign="top">

pct\_free



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The PCT\_FREE specification for the table, if one has been specified; otherwise, NULL.



</td>
</tr>
<tr>
<td valign="top">

clustered\_index\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The ID of the clustered index for the table. If none of the indexes are clustered, then this field is NULL.



</td>
</tr>
<tr>
<td valign="top">

encrypted



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Whether the table or materialized view is encrypted.



</td>
</tr>
<tr>
<td valign="top">

last\_modified\_tsn



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

A sequence number assigned to the transaction that modified the table. This column is only updated at checkpoint time.



</td>
</tr>
<tr>
<td valign="top">

current\_schema



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The current schema version of the table.



</td>
</tr>
<tr>
<td valign="top">

file\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

DEPRECATED. This column is present in SYSVIEW, but not in the underlying system table ISYSTAB. The contents of this column is the same as dbspace\_id and is provided for compatibility. Use dbspace\_id instead.



</td>
</tr>
<tr>
<td valign="top">

table\_type\_str



</td>
<td valign="top">

CHAR\(13\)



</td>
<td valign="top">

Readable value for table\_type. Values include:

 BASE
 :   Base table

  MAT VIEW
 :   Materialized view

  GBL TEMP
 :   Global temporary table

  VIEW
 :   View

 

</td>
</tr>
<tr>
<td valign="top">

last\_modified\_at\_utc



</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE



</td>
<td valign="top">

The UTC time at which the data in the table was last modified. This column is only updated at checkpoint time.



</td>
</tr>
</table>

**Related Information**  


[SYSTAB System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/9f67d02bffc5494fa10c6e2c245cd3ee.html "Each row of the SYSTAB system view describes one table or view in the database. Additional information for views can be found in the SYSVIEW system view. The underlying system table for this view is ISYSTAB.") :arrow_upper_right:

