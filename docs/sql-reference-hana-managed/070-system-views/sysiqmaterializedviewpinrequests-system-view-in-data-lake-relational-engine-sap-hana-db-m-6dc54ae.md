<!-- loio6dc54aef9f0f46edaea2bbe8c4970ca1 -->

# SYSIQMATERIALIZEDVIEWPINREQUESTS System View in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Displays the mapping of incremental refresh materialized views and all associated pin requests.



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

Column type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

view\_owner



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

Displays the owner of the materialized view.



</td>
</tr>
<tr>
<td valign="top">

view\_name



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

Displays the name of the materialized view.



</td>
</tr>
<tr>
<td valign="top">

pin\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Displays the ID of the pin request.



</td>
</tr>
</table>

