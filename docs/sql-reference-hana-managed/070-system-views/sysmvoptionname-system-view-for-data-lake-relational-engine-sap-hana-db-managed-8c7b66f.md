<!-- loio8c7b66fe90e64870b498bbb2071d3041 -->

# SYSMVOPTIONNAME System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSMVOPTIONNAME system view gives the name of an option that is stored for each materialized view at the time of its creation. The value for the option can be found in the SYSMVOPTION system view. The underlying system table for this view is ISYSMVOPTIONNAME.



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

option\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A number uniquely identifying the option in the database.



</td>
</tr>
<tr>
<td valign="top">

option\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the option.



</td>
</tr>
</table>

**Related Information**  


[SYSMVOPTIONNAME System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3be941066c5f1014b6f8dbc61db5c4f3.html "Each row in the SYSMVOPTIONNAME system view gives the name of an option that is stored for each materialized view at the time of its creation. The value for the option can be found in the SYSMVOPTION system view. The underlying system table for this view is ISYSMVOPTIONNAME.") :arrow_upper_right:

