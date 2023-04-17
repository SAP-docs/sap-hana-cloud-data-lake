<!-- loio96ce66486fbf4da3a705c8daa1dbc85f -->

# SYSUSERMESSAGE System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYS.SYSUSERMESSAGE system view holds a user-defined message for an error condition.



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

error



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

A unique identifying number for the error condition.



</td>
</tr>
<tr>
<td valign="top">

uid



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The user number that defined the message.



</td>
</tr>
<tr>
<td valign="top">

description



</td>
<td valign="top">

VARCHAR\(255\)



</td>
<td valign="top">

The message corresponding to the error condition.



</td>
</tr>
<tr>
<td valign="top">

langid



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Reserved.



</td>
</tr>
</table>

**Related Information**  


[SYSUSERMESSAGE System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3beb0a2a6c5f10149b6a8464d96325f5.html "Each row in the SYS.SYSUSERMESSAGE system view holds a user-defined message for an error condition.") :arrow_upper_right:

