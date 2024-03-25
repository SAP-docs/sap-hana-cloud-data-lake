<!-- loio3be5bff46c5f10149c2c85dc65723d6e -->

# sa\_eng\_properties System Procedure for Data Lake Relational Engine

Reports database server property information.



<a name="loio3be5bff46c5f10149c2c85dc65723d6e__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_eng_properties( )
```



<a name="loio3be5bff46c5f10149c2c85dc65723d6e__section_etq_kjm_zyb"/>

## Parameters

None



## Result Set


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

PropNum

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The database server property number.

</td>
</tr>
<tr>
<td valign="top">

PropName

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The database server property name.

</td>
</tr>
<tr>
<td valign="top">

PropDescription

</td>
<td valign="top">

VARCHAR\(255\)

</td>
<td valign="top">

The database server property description.

</td>
</tr>
<tr>
<td valign="top">

Value

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The database server property value.

</td>
</tr>
</table>



## Remarks

Returns the PropNum, PropName, PropDescription, and Value for each available server property. Values are returned for all database server properties and statistics related to database servers.



## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



## Examples

This example uses the sa\_eng\_properties system procedure to return a set of available server properties.

```
CALL sa_eng_properties( );
```


<table>
<tr>
<th valign="top">

PropNum

</th>
<th valign="top">

PropName

</th>
<th valign="top">

PropDescription

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

ActiveReq

</td>
<td valign="top">

Active requests

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

AvailIO

</td>
<td valign="top">

Number of available I/O control blocks

</td>
<td valign="top">

248

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

BytesReceived

</td>
<td valign="top">

Bytes received by server

</td>
<td valign="top">

507280567

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

BytesReceivedUncomp

</td>
<td valign="top">

Bytes received after decompression

</td>
<td valign="top">

507280567

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

BytesSent

</td>
<td valign="top">

Bytes sent to client

</td>
<td valign="top">

643008254

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

