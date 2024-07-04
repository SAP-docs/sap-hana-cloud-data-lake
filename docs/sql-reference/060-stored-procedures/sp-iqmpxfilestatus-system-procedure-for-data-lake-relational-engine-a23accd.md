<!-- loioa23accd884f210158ae2f17452390330 -->

# sp\_iqmpxfilestatus System Procedure for Data Lake Relational Engine

If run on the coordinator node, displays file status for the coordinator, and for every shared dbspace file on every included worker node. If executed on a worker node, displays file status for only the current node.



<a name="loioa23accd884f210158ae2f17452390330__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxfilestatus
```



<a name="loioa23accd884f210158ae2f17452390330__section_lm4_ppc_fbc"/>

## Parameters

None.



## Result Set


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

Requires EXECUTE object-level privilege on this procedure, along with MANAGE MULTIPLEX system privilege.



## Side Effects

None.



## Examples

This example returns file status information.

```
CALL sp_iqmpxfilestatus;
```


<table>
<tr>
<th valign="top">

server\_id

</th>
<th valign="top">

server\_name

</th>
<th valign="top">

DBSpace\_name

</th>
<th valign="top">

FileName

</th>
<th valign="top">

FileStatus

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

'mpx2422\_m'

</td>
<td valign="top">

'IQ\_SYSTEM\_MAIN'

</td>
<td valign="top">

'IQ\_SYSTEM\_MAIN'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

'mpx2422\_m'

</td>
<td valign="top">

'mpx\_main1'

</td>
<td valign="top">

'mpx\_main1'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

'mpx2422\_m'

</td>
<td valign="top">

'IQ\_SHARED\_TEMP'

</td>
<td valign="top">

'sharedfile\_dba'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

'mpx2422\_m'

</td>
<td valign="top">

'IQ\_SHARED\_TEMP'

</td>
<td valign="top">

'sharedfile\_dba1'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

'mpx2422\_w1'

</td>
<td valign="top">

'IQ\_SYSTEM\_MAIN'

</td>
<td valign="top">

'IQ\_SYSTEM\_MAIN'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

'mpx2422\_w1'

</td>
<td valign="top">

'mpx\_main1'

</td>
<td valign="top">

'mpx\_main1'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

'mpx2422\_w1'

</td>
<td valign="top">

'IQ\_SHARED\_TEMP'

</td>
<td valign="top">

'sharedfile\_dba'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

'mpx2422\_w1'

</td>
<td valign="top">

'IQ\_SHARED\_TEMP'

</td>
<td valign="top">

'sharedfile\_dba1'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

'mpx2422\_r1'

</td>
<td valign="top">

'IQ\_SYSTEM\_MAIN'

</td>
<td valign="top">

'IQ\_SYSTEM\_MAIN'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

'mpx2422\_r1'

</td>
<td valign="top">

'mpx\_main1'

</td>
<td valign="top">

'mpx\_main1'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

'mpx2422\_r1'

</td>
<td valign="top">

'IQ\_SHARED\_TEMP'

</td>
<td valign="top">

'sharedfile\_dba'

</td>
<td valign="top">

'VALID'

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

'mpx2422\_r1'

</td>
<td valign="top">

'IQ\_SHARED\_TEMP'

</td>
<td valign="top">

'sharedfile\_dba1'

</td>
<td valign="top">

'VALID'

</td>
</tr>
</table>

