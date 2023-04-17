<!-- loioa5d4d0f884f21015b5589652d668a182 -->

# SYSPARTITIONKEY System View for Data Lake Relational Engine

Presents group information from `ISYSPARTITIONKEY` in a readable format.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

Each partitioned object \(table\) is assigned a unique object number.



</td>
</tr>
<tr>
<td valign="top">

column\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The column ID identifies the table column as part of the partitioning key.



</td>
</tr>
<tr>
<td valign="top">

position



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Position of this column in the partitioning key. Position is 0 based. A position of 0 indicates the 1st column in the partitioning key.



</td>
</tr>
</table>



<a name="loioa5d4d0f884f21015b5589652d668a182__SYSPARTITIONKEY_remarks1"/>

## Remarks

Each row in the `SYSPARTITIONKEY` view describes a partitioned object \(table or index\) in the database.

```
ALTER VIEW "SYS"."SYSPARTITIONKEY"
as select * from SYS.ISYSPARTITIONKEY
```



<a name="loioa5d4d0f884f21015b5589652d668a182__SYSPARTITIONKEY_constraints1"/>

## Constraints on Underlying System Table

```
Primary key (partitioned_object_id, column_id)
```

```
Foreign key (partitioned_object_id) references SYS.ISYSOBJECT
```

**Related Information**  


[SYSPARTITIONKEY System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/6cde676a747347609a0c559e3324e62a.html "Presents group information from ISYSPARTITIONKEY in a readable format.") :arrow_upper_right:

