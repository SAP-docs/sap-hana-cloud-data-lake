<!-- loioa23accd884f210158ae2f17452390330 -->

# sp\_iqmpxfilestatus Procedure for Data Lake Relational Engine

If run on the coordinator node, displays file status for the coordinator, and for every shared dbspace file on every included worker node. If executed on a worker node, displays file status for only the current node.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxfilestatus
```



## Returns


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

server\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

Identifier for the multiplex node, from SYSIQMPXINFO



</td>
</tr>
<tr>
<td valign="top">

server\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the multiplex node where the dbspace file resides



</td>
</tr>
<tr>
<td valign="top">

dbspace\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Dbspace from which the space is reserved



</td>
</tr>
<tr>
<td valign="top">

dbfile\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Logical file name of the dbspace file



</td>
</tr>
<tr>
<td valign="top">

FileStatus



</td>
<td valign="top">

CHAR\(2\)



</td>
<td valign="top">

Dbspace file status:

-   VALID – file path and privileges are correct
-   INVALID\_PATH – can't access path name
-   INVALID\_PERM – file privileges are incorrect



</td>
</tr>
</table>



## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 

You also need:


<table>
<tr>
<th valign="top">

Privilege Name



</th>
<th valign="top">

Privilege Type



</th>
<th valign="top">

Grant Statement



</th>
</tr>
<tr>
<td valign="top">

MANAGE MULTIPLEX



</td>
<td valign="top">

System privilege



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



## Side Effects

None



## Example

The following shows sample output from sp\_iqmpxfilestatus:

```
server_id,server_name,DBSpace_name,FileName,FileStatus
1,'mpx2422_m','IQ_SYSTEM_MAIN','IQ_SYSTEM_MAIN','VALID'
1,'mpx2422_m','mpx_main1','mpx_main1','VALID'
1,'mpx2422_m','IQ_SHARED_TEMP','sharedfile_dba','VALID'
1,'mpx2422_m','IQ_SHARED_TEMP','sharedfile_dba1','VALID'
2,'mpx2422_w1','IQ_SYSTEM_MAIN','IQ_SYSTEM_MAIN','VALID'
2,'mpx2422_w1','mpx_main1','mpx_main1','VALID'
2,'mpx2422_w1','IQ_SHARED_TEMP','sharedfile_dba','VALID'
2,'mpx2422_w1','IQ_SHARED_TEMP','sharedfile_dba1','VALID'
3,'mpx2422_r1','IQ_SYSTEM_MAIN','IQ_SYSTEM_MAIN','VALID'
3,'mpx2422_r1','mpx_main1','mpx_main1','VALID'
3,'mpx2422_r1','IQ_SHARED_TEMP','sharedfile_dba','VALID'
3,'mpx2422_r1','IQ_SHARED_TEMP','sharedfile_dba1','VALID'
```

