<!-- loio3be7f6466c5f1014b874ecf96f287f38 -->

# SYSDEPENDENCY System View for Data Lake Relational Engine

Each row in the SYSDEPENDENCY system view describes a dependency between two database objects. The underlying system table for this view is ISYSDEPENDENCY.



<a name="loio3be7f6466c5f1014b874ecf96f287f38__section_bg3_c2q_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



A dependency exists between two database objects when one object references another object in its definition. For example, if the query specification for a view references a table, the view is dependent on the table. The database server tracks dependencies of views on tables, views, materialized views, and columns.


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

ref\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the referenced object.

</td>
</tr>
<tr>
<td valign="top">

dep\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The ID of the referencing object.

</td>
</tr>
</table>

**Related Information**  


[View Dependencies](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2024_1_QRC/en-US/7fbf3ca28b2e4c349d7a076cb2225a57.html "A view definition refers to other objects such as data lake Relational Engine columns, tables, and other views, and these references make the view dependent on the objects to which it refers.") :arrow_upper_right:

[sa\_dependent\_views System Procedure for Data Lake Relational Engine](../060-stored-procedures/sa-dependent-views-system-procedure-for-data-lake-relational-engine-3be5950.md "Returns the list of all dependent views for a given table or view.")

[SYSDEPENDENCY System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/0865e22dbe0a48d7ae56c62e5a7c57cd.html "Each row in the SYSDEPENDENCY system view describes a dependency between two database objects. The underlying system table for this view is ISYSDEPENDENCY.") :arrow_upper_right:

