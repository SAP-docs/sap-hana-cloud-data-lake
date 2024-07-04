<!-- loio3be595096c5f101489d8d608a7ef882e -->

# sa\_dependent\_views System Procedure for Data Lake Relational Engine

Returns the list of all dependent views for a given table or view.



<a name="loio3be595096c5f101489d8d608a7ef882e__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_dependent_views( [ '<table-name>' [, '{ <owner-name> | <schema-name> }' ] ] )
```



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_parm1"/>

## Parameters


<dl>
<dt><b>

*<table-name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the name of the table or view. The default is NULL.



</dd><dt><b>

*<owner-name\>* | *<schema-name\>*

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the owner or schema name for the *<table-name\>*. The default is NULL.



</dd>
</dl>



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_resultset1"/>

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



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_remarks1"/>

## Remarks

Use this procedure to obtain the list of IDs of tables and their dependent views.

No errors are generated if no existing tables satisfy the specified criteria for table and owner names. The following conditions also apply:

-   If both *<owner\>* or *<schema-name\>*  and *<table-name\>* are NULL, information is returned on all tables that have dependent views.

-   If *<table-name\>* is NULL but *<owner\>* or *<schema-name\>*  is specified, information is returned on all tables owned by the specified owner.

-   If *<table-name\>* is specified but *<owner\>* or *<schema-name\>*  is NULL, information is returned on any one of the tables with the specified name.




<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure. Also requires one of the following:

-   You own the underlying table of the view
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the view and its underlying tables
-   SELECT object-level privilege on the schema of the view and its underlying tables if the schema is owned by another user



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_sideefects1"/>

## Side Effects

None.



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_example1"/>

## Examples



### 

These examples assume the following objects exist:

```
--- Setup for the following examples ---
CREATE TABLE mytable (ColA int, ColB VARCHAR(10), ColC int);
CREATE VIEW V_mytable_A AS SELECT ColA FROM mytable;
CREATE VIEW V_mytable_B AS SELECT ColB FROM mytable;
CREATE VIEW V_mytable AS SELECT * FROM mytable;
```

This example returns the id's of the views dependent on the table mytable.

```
CALL sa_dependent_views( 'mytable' );
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

If you use the procedure in a SELECT statement, you can return the names of the dependent views.

```
SELECT t.table_name FROM SYSTAB t, sa_dependent_views( 'mytable' ) v 
WHERE t.table_id = v.dep_view_id;
```


<table>
<tr>
<th valign="top">

table\_name

</th>
</tr>
<tr>
<td valign="top">

V\_mytable\_A

</td>
</tr>
<tr>
<td valign="top">

V\_mytable\_B

</td>
</tr>
<tr>
<td valign="top">

V\_mytable

</td>
</tr>
</table>

**Related Information**  


[sa_dependent_views System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/47783e3af31b4f27a28b41ad534f8332.html "Returns the list of all dependent views for a given table or view.") :arrow_upper_right:

