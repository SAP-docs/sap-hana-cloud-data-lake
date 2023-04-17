<!-- loio90b394367905418082ba6886c9731975 -->

# BITMAP\_COUNT\_ALGORITHM Option for Data Lake Relational Engine

Controls the algorithm that is used by stored procedures such as sp\_iqfile and sp\_iqdbspace that report space utilization in the underlying database files.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio90b394367905418082ba6886c9731975__section_u1n_l5b_qkb"/>

## Syntax

```
BITMAP_COUNT_ALGORITHM = <value>
```



## Allowed Values

0 – System dynamically switches between the optimal algorithm as it scans the underlying database files.

1 – System is forced to use the algorithm that is optimized for computing space utilization over sparse regions in database files.

2 – System is forced to use the algorithm that is optimized for computing space utilization over dense regions in database files.



<a name="loio90b394367905418082ba6886c9731975__section_iqw_cts_qpb"/>

## Default

0



<a name="loio90b394367905418082ba6886c9731975__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: SYSTEM

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loio90b394367905418082ba6886c9731975__section_mvr_dts_qpb"/>

## Scope


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

PUBLIC Role



</th>
<th valign="top">

For Current User



</th>
<th valign="top">

For Other Users



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

**Related Information**  


[sp\_iqfile Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqfile-procedure-for-data-lake-relational-engine-a5a8f31.md "Displays detailed information about each dbfile in a dbspace.")

[sp\_iqdbspace Procedure for Data Lake Relational Engine](../060-stored-procedures/sp-iqdbspace-procedure-for-data-lake-relational-engine-a5a34b5.md "Displays detailed information about each data lake Relational Engine dbspace.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

