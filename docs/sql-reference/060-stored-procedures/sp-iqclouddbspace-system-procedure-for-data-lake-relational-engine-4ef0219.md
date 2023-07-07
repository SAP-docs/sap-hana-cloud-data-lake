<!-- loio4ef0219c16ec4f578395e34785797cfe -->

# sp\_iqclouddbspace System Procedure for Data Lake Relational Engine

Displays detailed information about the cloud dbspace in data lake Relational Engine.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqclouddbspace
```



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_returns1"/>

## Returns


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

The name of the cloud dbspace.



</td>
</tr>
<tr>
<td valign="top">

DbspaceID



</td>
<td valign="top">

The identifier of the cloud dbspace.



</td>
</tr>
<tr>
<td valign="top">

CurrSizeByte



</td>
<td valign="top">

The current size of the cloud dbspace in bytes.



</td>
</tr>
<tr>
<td valign="top">

MaxSizeByte



</td>
<td valign="top">

The maximum size of the cloud dbspace in bytes. A value of 0 indicates no size restriction.



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



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loio4ef0219c16ec4f578395e34785797cfe__sp_iqclouddbspace_example1"/>

## Example


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


[Cloud Dbspaces](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_2_QRC/en-US/493eb818429e4996b3da4153192a9efa.html "Cloud dbspace is a new offering where the database engine stores a user dbspace in object storage solutions such as Microsoft Azure Blob Storage, AWS Simple Storage Service (S3), or Google Cloud Storage. In a cloud dbspace, database pages are physically stored as objects as opposed to regular file system blocks.") :arrow_upper_right:

[sp_iqclouddbspace System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/4240c9a98ce04c2cb85a37ada268acb4.html "") :arrow_upper_right:

