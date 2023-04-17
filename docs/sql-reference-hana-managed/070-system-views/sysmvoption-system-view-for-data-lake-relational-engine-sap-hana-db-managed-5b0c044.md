<!-- loio5b0c044c69034850a8d3006feb79ce7f -->

# SYSMVOPTION System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYSMVOPTION system view describes the setting of one option value for a materialized viewor text index at the time of its creation. The name of the option can be found in the SYSMVOPTIONNAME system view. The underlying system table for this view is ISYSMVOPTION.



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

view\_object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The object ID of the materialized view.



</td>
</tr>
<tr>
<td valign="top">

option\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A unique number identifying the option in the database. To see the option name, see the SYSMVOPTIONNAME system view.



</td>
</tr>
<tr>
<td valign="top">

option\_value



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The value of the option when the materialized view was created.



</td>
</tr>
</table>

**Related Information**  


[SYSMVOPTION System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3be939606c5f1014a581c83fbbc9b790.html "Each row in the SYSMVOPTION system view describes the setting of one option value for a materialized view or text index at the time of its creation. The name of the option can be found in the SYSMVOPTIONNAME system view. The underlying system table for this view is ISYSMVOPTION.") :arrow_upper_right:

