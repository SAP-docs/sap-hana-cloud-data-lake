<!-- loioa4dae35184f2101588029fbd62f9bf43 -->

# sp\_iqmpxinfo Procedure for Data Lake Relational Engine

Returns a row for every node in the multiplex. Can be run from any multiplex node.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxinfo
```



<a name="loioa4dae35184f2101588029fbd62f9bf43__iq_iqmpx_252"/>

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

Identifier for the node for which information appears



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

Name of the node



</td>
</tr>
<tr>
<td valign="top">

connection\_info



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

A formatted string containing the host/port portion of the connection string used for TCP/IP connections between multiplex nodes.



</td>
</tr>
<tr>
<td valign="top">

db\_path



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Full database path



</td>
</tr>
<tr>
<td valign="top">

role



</td>
<td valign="top">

CHAR\(16\)



</td>
<td valign="top">

Values:

-   'coordinator'
-   'writer'
-   'reader'



</td>
</tr>
<tr>
<td valign="top">

status



</td>
<td valign="top">

CHAR\(8\)



</td>
<td valign="top">

Values:

-   'included'
-   'excluded'



</td>
</tr>
<tr>
<td valign="top">

mpx\_mode



</td>
<td valign="top">

CHAR\(16\)



</td>
<td valign="top">

Values:

-   'single'
-   'coordinator'
-   'writer'
-   'reader'
-   'unknown'



</td>
</tr>
<tr>
<td valign="top">

inc\_state



</td>
<td valign="top">

CHAR\(16\)



</td>
<td valign="top">

Values:

-   'active'
-   'not responding'
-   'timed out'



</td>
</tr>
<tr>
<td valign="top">

coordinator\_failover



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

Name of the failover node



</td>
</tr>
<tr>
<td valign="top">

current\_version



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

Decimal-formatted version ID



</td>
</tr>
<tr>
<td valign="top">

active\_versions



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Comma-separated list of decimal formatted version IDs.



</td>
</tr>
<tr>
<td valign="top">

private\_connection\_info



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

A formatted string containing the host/port portion of the connection string used for private TCP/IP connections between multiplex nodes



</td>
</tr>
<tr>
<td valign="top">

mipc\_priv\_state



</td>
<td valign="top">

CHAR\(16\)



</td>
<td valign="top">

Values:

-   'active' – MIPC connection to this node is active over the private interconnect
-   'not responding' – MIPC connection to this node isn't responding over private interconnect



</td>
</tr>
<tr>
<td valign="top">

mipc\_public\_state



</td>
<td valign="top">

CHAR\(16\)



</td>
<td valign="top">

Values:

-   'active' – MIPC connection to this node is active over the public interconnect
-   'not responding' – MIPC connection to this node isn't responding over public interconnect



</td>
</tr>
</table>



<a name="loioa4dae35184f2101588029fbd62f9bf43__iq_iqmpx_253"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). 

You also need one of the following:


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

-   MANAGE MULTIPLEX
-   MONITOR



</td>
<td valign="top">

System privileges



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



<a name="loioa4dae35184f2101588029fbd62f9bf43__section_xzz_crg_nbb"/>

## Side Effects

None



<a name="loioa4dae35184f2101588029fbd62f9bf43__iq_iqmpx_256"/>

## Example

The following shows sample output from sp\_iqmpxinfo:

```
server_id,server_name,connection_info,db_path,role,
status,mpx_mode,inc_state,coordinator_failover,
current_version,active_versions,private_connection_
info,mipc_priv_state,mipc_public_state
                                                                
1,'my_mpx1','host=(fe80::214:4fff:fe45:be26%2):1362
0,(fd77:55d:59d9:329:214:4fff:fe45:be2
6%2):13620,10.18.41.196:13620','/system3/users
/devices/s16900269/iqmpx1/mpx1.db',
'coordinator','included','coordinator','N/A',
'my_mpx2',0,,,'active','active'
                                                                
2,'IQ_mpx2','host=system3:13625',
'/system3/users/devices/s16900269
/iqmpx_2/wk0001.db','writer','included',
'writer','active','IQ_mpx20', 'not responding','active'
                                                                
3,'IQ_mpx3,'host=system3:13630/system3/users/devi
ces/s16900269/iqmpx_3/mpx1.db','reader','included',
'unknown',timed out',
'IQ_mpx20','not responding',
'not responding'
```

