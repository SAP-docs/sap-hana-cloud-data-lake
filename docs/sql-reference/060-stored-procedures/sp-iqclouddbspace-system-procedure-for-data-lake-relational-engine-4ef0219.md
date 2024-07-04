<!-- loio4ef0219c16ec4f578395e34785797cfe -->

# sp\_iqclouddbspace System Procedure for Data Lake Relational Engine

Displays information about the user\_object\_store dbspace.



<a name="loio4ef0219c16ec4f578395e34785797cfe__section_rpg_3dw_f4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqclouddbspace()
```



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_param1"/>

## Parameters

None.



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_returns1"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

DbspaceName

</td>
<td valign="top">

The name of the dbspace.

</td>
</tr>
<tr>
<td valign="top">

DbspaceID

</td>
<td valign="top">

The identifier of the dbspace.

</td>
</tr>
<tr>
<td valign="top">

CurrSizeByte

</td>
<td valign="top">

The current size of the dbspace in bytes.

</td>
</tr>
<tr>
<td valign="top">

MaxSizeByte

</td>
<td valign="top">

The maximum size of the dbspace in bytes. A value of 0 indicates no size restriction.

</td>
</tr>
<tr>
<td valign="top">

PageSizeByte

</td>
<td valign="top">

The size of a database page in bytes. This is calculated based on the compression ratio and the number of pages used.

</td>
</tr>
</table>



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_remarks1"/>

## Remarks

The sizes that this procedure outputs are estimations based on heuristics, not an accurate number. They are an estimation only.



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_example1"/>

## Examples

This example returns information on the dbspace user\_object\_store.

```
CALL sp_iqclouddbspace();
```


<table>
<tr>
<th valign="top">

DbspaceName

</th>
<th valign="top">

DbspaceID

</th>
<th valign="top">

CurrSizeByte

</th>
<th valign="top">

MaxSizeByte

</th>
<th valign="top">

PageSizeByte

</th>
</tr>
<tr>
<td valign="top">

user\_object\_store

</td>
<td valign="top">

16388

</td>
<td valign="top">

131072

</td>
<td valign="top">

0

</td>
<td valign="top">

65536

</td>
</tr>
</table>

**Related Information**  


[sp_iqclouddbspace System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/4240c9a98ce04c2cb85a37ada268acb4.html "Displays information about the user_object_store dbspace.") :arrow_upper_right:

