<!-- loiod5978ec7e26643178577c42bcecb6c64 -->

# SYSJWTLOGINMAP System View for Data Lake Relational Engine

Lists the JWT-user mappings configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTLOGINMAP.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

login\_id



</td>
<td valign="top">

VARCHAR\(1024\)



</td>
<td valign="top">

The name of the user known to the JWT provider.



</td>
</tr>
<tr>
<td valign="top">

jwt\_provider\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The ID of the JWT provider.



</td>
</tr>
<tr>
<td valign="top">

database\_uid



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The data lake Relational Engine database user ID to which login\_id is mapped.



</td>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

A unique identifier for the mapping.



</td>
</tr>
</table>

**Related Information**  


[SYSJWTPROVIDERS System View for Data Lake Relational Engine](sysjwtproviders-system-view-for-data-lake-relational-engine-40fe6b4.md "Lists JWT providers configured in the data lake Relational Engine database. The underlying system table for this view is ISYSJWTPROVIDERS.")

