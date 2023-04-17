<!-- loio8387df93bb6c4a87acd9138dbaa18ba9 -->

# SYSIQTABCOL System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from `ISYSIQTABCOL` in a readable format. Each row in the SYSIQTABCOL view describes a column in an IQ table.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Viewing System Views](remote-execute-usage-examples-for-viewing-system-views-8b235c7.md).
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE\_QUERY procedure.
> 
>     -   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](remote-execute-query-usage-examples-for-viewing-system-views-ada51c0.md).



> ### Note:  
> This view replaces the deprecated system view SYSIQCOLUMN.


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Column Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

link\_table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

link\_column\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For internal use.



</td>
</tr>
<tr>
<td valign="top">

max\_length



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

Indicates the maximum length allowed by the column.



</td>
</tr>
<tr>
<td valign="top">

approx\_unique\_count



</td>
<td valign="top">

ROWID



</td>
<td valign="top">

Approximate number of unique values \(cardinality\) of this column.



</td>
</tr>
<tr>
<td valign="top">

cardinality



</td>
<td valign="top">

ROWID



</td>
<td valign="top">

The actual number of unique values \(cardinality\) of this column.



</td>
</tr>
<tr>
<td valign="top">

has\_data



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates that the column contains data \(T/F\).



</td>
</tr>
<tr>
<td valign="top">

is\_nbit



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates whether the column is NBit \(T\) or Flat FP \(F\).



</td>
</tr>
</table>



<a name="loio8387df93bb6c4a87acd9138dbaa18ba9__section_id5_dtj_wrb"/>

## Remarks

```
ALTER VIEW "SYS"."SYSIQTABCOL"
                    as select * from SYS.ISYSIQTABCOL
```



<a name="loio8387df93bb6c4a87acd9138dbaa18ba9__section_ik2_2tj_wrb"/>

## Constraints on Underlying System Table

```
Primary key (table_id)
```

**Related Information**  


[SYSIQTABCOL System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5d1bd5684f2101581e2c9c8b4c4669b.html "Presents group information from ISYSIQTABCOL in a readable format. Each row in the SYSIQTABCOL view describes a column in an IQ table.") :arrow_upper_right:

