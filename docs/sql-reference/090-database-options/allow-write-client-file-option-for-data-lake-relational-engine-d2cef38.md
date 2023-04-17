<!-- loiod2cef385fd984a97a80a5ac5b9615fe6 -->

# ALLOW\_WRITE\_CLIENT\_FILE Option for Data Lake Relational Engine

Controls whether to allow the writing of files to a client computer.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loiod2cef385fd984a97a80a5ac5b9615fe6__section_u1n_l5b_qkb"/>

## Syntax

```
ALLOW_WRITE_CLIENT_FILE  = { ON | OFF }
```



<a name="loiod2cef385fd984a97a80a5ac5b9615fe6__section_enp_y1g_x4b"/>

## Allowed Values

ON, OFF



<a name="loiod2cef385fd984a97a80a5ac5b9615fe6__section_fnp_y1g_x4b"/>

## Default

OFF



<a name="loiod2cef385fd984a97a80a5ac5b9615fe6__section_eym_3fc_3qb"/>

## Privileges

Privilege Category: SECURITY

Requires the SET ANY CUSTOMER SECURITY OPTION system privilege to set this database option.



<a name="loiod2cef385fd984a97a80a5ac5b9615fe6__allow-write-client-file-option-scope"/>

## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC role



</th>
<th valign="top">

For current user



</th>
<th valign="top">

For other users



</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes \(current connection only\)



</td>
<td valign="top">

No



</td>
</tr>
</table>



<a name="loiod2cef385fd984a97a80a5ac5b9615fe6__section_gnp_y1g_x4b"/>

## Remarks

Enable this option to write files to a client computer, for example, by using the WRITE\_CLIENT\_FILE function.

Writing client files is not supported by the **Tabular Data Stream** \(**TDS**\) protocol.

