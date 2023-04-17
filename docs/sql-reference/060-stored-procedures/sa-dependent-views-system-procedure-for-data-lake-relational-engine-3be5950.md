<!-- loio3be595096c5f101489d8d608a7ef882e -->

# sa\_dependent\_views System Procedure for Data Lake Relational Engine

Returns the list of all dependent views for a given table or view.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_dependent_views( 
[ <tbl_name> 
[, <owner_name> ] ] 
)
```



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_parm1"/>

## Parameters

  *<tbl\_name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the name of the table or view. The default is NULL.

   *<owner\_name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the owner for *<tbl\_name\>*. The default is NULL.

 

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

-   If both *<owner\>* and *<tbl\_name\>* are NULL, information is returned on all tables that have dependent views.

-   If *<tbl\_name\>* is NULL but *<owner\>* is specified, information is returned on all tables owned by the specified owner.

-   If *<tbl\_name\>* is specified but *<owner\>* is NULL, information is returned on any one of the tables with the specified name.




<a name="loio3be595096c5f101489d8d608a7ef882e__section_a2g_rcj_snb"/>

## Privileges

You need to have the EXECUTE privilege on the system procedure.



<a name="loio3be595096c5f101489d8d608a7ef882e__sa_dependent_views_sideefects1"/>

## Side Effects

None



In this example, the sa\_dependent\_views system procedure is used to obtain the list of IDs for the views that are dependent on the SalesOrders table. The procedure returns the table\_id for SalesOrders, and the dep\_view\_id for the dependent view, ViewSalesOrders.

```
CALL sa_dependent_views( 'SalesOrders' );
```

In this example, the sa\_dependent\_views system procedure is used in a SELECT statement to obtain the list of names of views dependent on the SalesOrders table. The procedure returns the ViewSalesOrders view.

```
SELECT t.table_name FROM SYSTAB t,  
sa_dependent_views( 'SalesOrders' ) v 
WHERE t.table_id = v.dep_view_id;
```

**Related Information**  


[sa_dependent_views System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/47783e3af31b4f27a28b41ad534f8332.html "Returns the list of all dependent views for a given table or view.") :arrow_upper_right:

