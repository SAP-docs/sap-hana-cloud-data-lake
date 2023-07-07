<!-- loio3beb0a2a6c5f10149b6a8464d96325f5 -->

# SYSUSERMESSAGE System View for Data Lake Relational Engine

Each row in the SYS.SYSUSERMESSAGE system view holds a user-defined message for an error condition.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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


[SYSUSERMESSAGE System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/96ce66486fbf4da3a705c8daa1dbc85f.html "Each row in the SYS.SYSUSERMESSAGE system view holds a user-defined message for an error condition.") :arrow_upper_right:

