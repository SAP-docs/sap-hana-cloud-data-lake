<!-- loio47783e3af31b4f27a28b41ad534f8332 -->

# sa\_dependent\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the list of all dependent views for a given table or view.



<a name="loio47783e3af31b4f27a28b41ad534f8332__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_dependent_views( [ '<table-name>' , '<schema-name>' ] )
```



<a name="loio47783e3af31b4f27a28b41ad534f8332__section_ygz_n54_rrb"/>

## Parameters


<dl>
<dt><b>

*<table-name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the name of the table or view. The default is NULL.



</dd><dt><b>

*<schema-name\>* 

</b></dt>
<dd>

Specify the user-created schema name for the *<table-name\>*. The referenced table must reside in a user-created schema in a relational container. It cannot reside in the default schema \(SYSHDL\_*<relational\_container\_name\>*\).



</dd>
</dl>



<a name="loio47783e3af31b4f27a28b41ad534f8332__section_qrn_454_rrb"/>

## Result Set


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

UNSIGNED INTEGER

</td>
<td valign="top">

The object ID of the table or view.

</td>
</tr>
<tr>
<td valign="top">

dep\_view\_id

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The object ID of the dependent views.

</td>
</tr>
</table>



<a name="loio47783e3af31b4f27a28b41ad534f8332__section_zd2_p54_rrb"/>

## Remarks

When directly connected to data lake Relational Engine, the table specified must be in a user-created schema in the relational container. It cannot be in the default relational container schema \(SYSHDL\_*<relational\_container\_name\>*\).

Use this procedure to obtain the list of IDs of tables and their dependent views.

No errors are generated if no existing tables satisfy the specified criteria for table and owner names. The following conditions also apply:

-   If both *<schema-name\>* and *<table-name\>* are NULL, information is returned on all tables that have dependent views.

-   If *<table-name\>* is NULL but *<schema-name\>* is is specified, information is returned on all tables owned by the specified owner.

-   If *<table-name\>* is specified but *<schema-name\>* is NULL, information is returned on any one of the tables with the specified name.




<a name="loio47783e3af31b4f27a28b41ad534f8332__section_zm1_31b_1yb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using REMOTE\_EXECUTE\_QUERY:

</b></dt>
<dd>

Requires the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Guidance and Examples for Running Stored Procedures](remote-execute-query-guidance-and-examples-for-running-stored-procedures-3e7f86d.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires EXECUTE object-level privilege on this procedure. Also requires one of the following:

-   You own the underlying table of the view
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the view and its underlying tables
-   SELECT object-level privilege on the schema of the view and its underlying tables if the schema is owned by another user



</dd>
</dl>



<a name="loio47783e3af31b4f27a28b41ad534f8332__section_cf1_q54_rrb"/>

## Side Effects

None.



## Examples



### 

This example returns the id's of the views dependent on the table mytable. mytable is in the user-created schema myschema1 in relational containerSYSHDL\_CONTAINER1.

```
CALL sa_dependent_views( 'mytable','SYSHDL_CONTAINER1_MYSCHEMA1' );
```


<table>
<tr>
<th valign="top">

table\_id

</th>
<th valign="top">

dep\_view\_id

</th>
</tr>
<tr>
<td valign="top">

1783

</td>
<td valign="top">

1784

</td>
</tr>
<tr>
<td valign="top">

1783

</td>
<td valign="top">

1785

</td>
</tr>
<tr>
<td valign="top">

1783

</td>
<td valign="top">

1787

</td>
</tr>
</table>

**Related Information**  


[sa_dependent_views System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3be595096c5f101489d8d608a7ef882e.html "Returns the list of all dependent views for a given table or view.") :arrow_upper_right:

