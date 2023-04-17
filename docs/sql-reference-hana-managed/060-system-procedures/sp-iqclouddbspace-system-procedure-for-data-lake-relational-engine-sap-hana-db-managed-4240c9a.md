<!-- loio4240c9a98ce04c2cb85a37ada268acb4 -->

# sp\_iqclouddbspace System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)



```
sp_iqclouddbspace
```



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](../030-sql-statements/remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_e44_53r_pvb"/>

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



<a name="loio4240c9a98ce04c2cb85a37ada268acb4__iq_refbb_1703"/>

## Privileges

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:

 Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure:
 :   You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

  Connected directly to data lake Relational Engine as a data lake Relational Engine user:
 :   To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a3e154f084f21015996d891a5e9d33d2.html "Grants database object-level privileges on individual objects and schemas to a user or role.") :arrow_upper_right:.

 

<a name="loio4240c9a98ce04c2cb85a37ada268acb4__section_n5j_v3r_pvb"/>

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


[Cloud Dbspaces](https://help.sap.com/viewer/a896c6a184f21015b5bcf4c7a967df07/2023_1_QRC/en-US/493eb818429e4996b3da4153192a9efa.html "Cloud dbspace is a new offering where the database engine stores a user dbspace in object storage solutions such as Microsoft Azure Blob Storage, AWS Simple Storage Service (S3), or Google Cloud Storage. In a cloud dbspace, database pages are physically stored as objects as opposed to regular file system blocks.") :arrow_upper_right:

[sp_iqclouddbspace System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/4ef0219c16ec4f578395e34785797cfe.html "Displays detailed information about the cloud dbspace in data lake Relational Engine.") :arrow_upper_right:

