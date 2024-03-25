<!-- loio4240c9a98ce04c2cb85a37ada268acb4 -->

# sp\_iqclouddbspace System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Displays detailed information about the user\_object\_store dbspace.



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqclouddbspace()
```



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_yfd_p1y_tzb"/>

## Parameters

None



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_e44_53r_pvb"/>

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



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_emv_x1y_tzb"/>

## Remarks

None



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_psc_lw1_1yb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE\_QUERY Guidance and Examples for Running Stored Procedures](remote-execute-query-guidance-and-examples-for-running-stored-procedures-3e7f86d.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

-   Requires EXECUTE object-level privilege on the procedure.



</dd>
</dl>



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_n5j_v3r_pvb"/>

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


[Cloud Dbspaces](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2024_1_QRC/en-US/493eb818429e4996b3da4153192a9efa.html "In a cloud dbspace, the database engine stores a user dbspace in object storage solutions such as Microsoft Azure Blob Storage, AWS Simple Storage Service (S3), or Google Cloud Storage. In a cloud dbspace, database pages are physically stored as objects as opposed to regular file system blocks.") :arrow_upper_right:

[sp_iqclouddbspace System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/4ef0219c16ec4f578395e34785797cfe.html "Displays detailed information about the user_object_store dbspace.") :arrow_upper_right:

