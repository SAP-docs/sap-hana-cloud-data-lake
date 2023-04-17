<!-- loio7f6192e6d8db4a6da37fb888e0afcd62 -->

# SYSCONSTRAINT System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYS.SYSCONSTRAINT system view describes a named constraint in the database. The underlying system table for this view is ISYSCONSTRAINT.



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

constraint\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The unique ID for the constraint.



</td>
</tr>
<tr>
<td valign="top">

constraint\_type



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

The type of constraint:

 C
 :   column check constraint

  T
 :   table constraint

  P
 :   primary key

  F
 :   foreign key

  U
 :   unique constraint

 

</td>
</tr>
<tr>
<td valign="top">

ref\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the column, table, or index to which the constraint applies.



</td>
</tr>
<tr>
<td valign="top">

table\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the table to which the constraint applies.



</td>
</tr>
<tr>
<td valign="top">

constraint\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the constraint.



</td>
</tr>
</table>

**Related Information**  


[SYSCONSTRAINT System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3be757ac6c5f1014ace0e4235b05fb2d.html "Each row in the SYS.SYSCONSTRAINT system view describes a named constraint in the database. The underlying system table for this view is ISYSCONSTRAINT.") :arrow_upper_right:
