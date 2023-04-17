<!-- loio4f05e41823a145a4812e4bb783bdc650 -->

# SYSPARTITIONSCHEME System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Presents group information from `ISYSPARTITIONSCHEME` in a readable format.



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

partitioned\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Each partitioned object \(table\) is assigned a unique number.



</td>
</tr>
<tr>
<td valign="top">

partition\_method



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Partitioning method for this table. Valid values:

-   1 – for range
-   3 – for hash \(2 is unused\)



</td>
</tr>
<tr>
<td valign="top">

subpartition\_method



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Subpartitioning method for this table. Valid values:

-   NULL - no subpartitioning
-   1 – for range partitioning
-   3 – for hash partitioning \(2 is unused\)



</td>
</tr>
</table>



<a name="loio4f05e41823a145a4812e4bb783bdc650__section_qkl_drj_wrb"/>

## Remarks

Each row in the `SYSPARTITIONSCHEME` view describes a partitioned object \(table or index\) in the database.

```
ALTER VIEW "SYS"."SYSPARTITIONSCHEME"
as select * from SYS.ISYSPARTITIONSCHEME
```



<a name="loio4f05e41823a145a4812e4bb783bdc650__section_rjx_drj_wrb"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id)
```

```
Foreign key (partitioned_object_id) references SYS.ISYSOBJECT
```

**Related Information**  


[SYSPARTITIONSCHEME System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a5d551b784f21015b3eabb10e5074fd2.html "Presents group information from ISYSPARTITIONSCHEME in a readable format.") :arrow_upper_right:

