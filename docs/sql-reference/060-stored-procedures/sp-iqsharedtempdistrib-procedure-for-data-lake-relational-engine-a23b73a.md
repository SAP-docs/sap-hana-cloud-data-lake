<!-- loioa23b73a584f2101597cbaf0fec393cb7 -->

# sp\_iqsharedtempdistrib Procedure for Data Lake Relational Engine

Shows the current shared temp space usage distribution. If run from the coordinator, sp\_iqsharedtempdistrib displays shared temp space distribution for all nodes. If run from a worker node, displays shared temp space usage for only that node.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqsharedtempdistrib
```



## Returns


<table>
<tr>
<th valign="top">

Column



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

Server\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

ID of the multiplex node, from SYSIQMPXINFO.



</td>
</tr>
<tr>
<td valign="top">

DBSpace\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the dbspace from which space is reserved.



</td>
</tr>
<tr>
<td valign="top">

Unit\_type



</td>
<td valign="top">

CHAR\(10\)



</td>
<td valign="top">

Type of allocation unit. Valid values are:

-   Active – currently reserved and in use by the node.
-   Expired – reserved for the node but in transition back to the global space pool.
-   Quarantined – reserved for the node but quarantined because of node failure.



</td>
</tr>
<tr>
<td valign="top">

VersionID



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Version ID of the unit. For active units, the version when the unit was reserved for the node. For expired units, the version when the unit was expired. For quarantined units, the version when the unit was quarantined.



</td>
</tr>
<tr>
<td valign="top">

NBlocks



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Number of outstanding blocks in the unit.



</td>
</tr>
</table>



<a name="loioa23b73a584f2101597cbaf0fec393cb7__section_h41_jd4_nbb"/>

## Remarks

Shared temporary space is reserved for each node in the multiplex on demand. Space is reserved for a node in an allocation unit. Nodes can have multiple allocation units reserved based on their dynamic space demands. Allocation units are leased to allow nodes to use more space as needed and return the space to a global pool when not needed. Allocation units expire when space usage decreases and their lease time ends, or when a node shuts down.



<a name="loioa23b73a584f2101597cbaf0fec393cb7__section_lbf_gm5_xxb"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure, along with MANAGE ANY DBSPACE system privilege.



## Side Effects

None

