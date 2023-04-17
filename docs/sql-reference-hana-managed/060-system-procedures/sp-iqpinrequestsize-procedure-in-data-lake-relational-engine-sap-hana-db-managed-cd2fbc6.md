<!-- loiocd2fbc63744f47b28252976bc905b684 -->

# sp\_iqpinrequestsize Procedure in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the mapping of pin requests to the maximum releaseable size in kilobytes.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sp_iqpinrequestsize()
```



<a name="loiocd2fbc63744f47b28252976bc905b684__section_w2g_zdb_hwb"/>

## Returns

Returns the mapping of pin requests to the maximum releaseable size in kilobytes.


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

pin\_id



</td>
<td valign="top">

Displays the ID of the pin request.



</td>
</tr>
<tr>
<td valign="top">

max\_kb\_release



</td>
<td valign="top">

Displays the maximum size, in kilobytes, to be released if the pin request is deleted.



</td>
</tr>
</table>



<a name="loiocd2fbc63744f47b28252976bc905b684__section_v5t_zdb_hwb"/>

## Remarks

sp\_iqpinrequestsize can only be run on the coordinator node. The coordinator endpoint can be found on the *Action* menu for the instance in SAP HANA Cloud Central.

