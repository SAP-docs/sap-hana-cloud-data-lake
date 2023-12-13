<!-- loio0865e22dbe0a48d7ae56c62e5a7c57cd -->

# SYSDEPENDENCY System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSDEPENDENCY system view describes a dependency between two database objects. The underlying system table for this view is ISYSDEPENDENCY.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.




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



<a name="loio0865e22dbe0a48d7ae56c62e5a7c57cd__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[View Dependencies in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_4_QRC/en-US/819c42256ce21014bb5faa0cc1d6fdb8.html "A view definition refers to other objects such as data lake Relational Engine columns, tables, and other views, and these references make the view dependent on the objects to which it refers.") :arrow_upper_right:

[sa\_dependent\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../060-system-procedures/sa-dependent-views-system-procedure-for-data-lake-relational-engine-sap-hana-db-managed-47783e3.md "Returns the list of all dependent views for a given table or view.")

[SYSDEPENDENCY System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3be7f6466c5f1014b874ecf96f287f38.html "Each row in the SYSDEPENDENCY system view describes a dependency between two database objects. The underlying system table for this view is ISYSDEPENDENCY.") :arrow_upper_right:

