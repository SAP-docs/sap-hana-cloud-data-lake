<!-- loio3be9e67e6c5f10148d62c6cd2ae10104 -->

# SYSREMOTEOPTIONTYPE System View for Data Lake Relational Engine

Each row in the SYSREMOTEOPTIONTYPE system view describes one of the message link parameters. The underlying system table for this view is ISYSREMOTEOPTIONTYPE.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column



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

An identification number for the message link parameter.



</td>
</tr>
<tr>
<td valign="top">

type\_id



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

An identification number for the message type that uses the parameter.



</td>
</tr>
<tr>
<td valign="top">

option



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The name of the message link parameter.



</td>
</tr>
</table>



## Constraints on Underlying System Table

```
PRIMARY KEY (option_id)
```

```
FOREIGN KEY (type_id) REFERENCES SYS.ISYSREMOTETYPE (type_id)
```

