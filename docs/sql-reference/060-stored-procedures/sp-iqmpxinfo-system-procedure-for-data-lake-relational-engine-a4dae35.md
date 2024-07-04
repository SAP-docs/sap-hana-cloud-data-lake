<!-- loioa4dae35184f2101588029fbd62f9bf43 -->

# sp\_iqmpxinfo System Procedure for Data Lake Relational Engine

Returns a row for every node in the multiplex. Can be run from any multiplex node.



<a name="loioa4dae35184f2101588029fbd62f9bf43__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxinfo
```



<a name="loioa4dae35184f2101588029fbd62f9bf43__section_lm4_ppc_fbc"/>

## Parameters

None.



<a name="loioa4dae35184f2101588029fbd62f9bf43__iq_iqmpx_252"/>

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

Requires EXECUTE object-level privilege on this procedure, along with the MONITOR system privilege



<a name="loioa4dae35184f2101588029fbd62f9bf43__section_xzz_crg_nbb"/>

## Side Effects

None.



<a name="loioa4dae35184f2101588029fbd62f9bf43__iq_iqmpx_256"/>

## Examples

This example returns a row for each node in the multiplex.

```
CALL sp_iqmpxinfo;
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

connection\_info

</th>
<th valign="top">

db\_path

</th>
<th valign="top">

role

</th>
<th valign="top">

status

</th>
<th valign="top">

mpx\_mode

</th>
<th valign="top">

inc\_

state

</th>
<th valign="top">

...

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

mpx-coord-0

</td>
<td valign="top">

host=mpx-coord-0.mpx-coord.XXX.local:2638

</td>
<td valign="top">

/data\_shared/coord/iqaas.db

</td>
<td valign="top">

coordinator

</td>
<td valign="top">

included

</td>
<td valign="top">

coordinator

</td>
<td valign="top">

N/A

</td>
<td valign="top">

...

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

mpx-writer-0-0

</td>
<td valign="top">

host=mpx-writer-0-0.mpx-writer.XXX.local:2638

</td>
<td valign="top">

/data\_local/mpx-writer-0-0/iqaas.db

</td>
<td valign="top">

writer

</td>
<td valign="top">

included

</td>
<td valign="top">

writer

</td>
<td valign="top">

active

</td>
<td valign="top">

...

</td>
</tr>
</table>

