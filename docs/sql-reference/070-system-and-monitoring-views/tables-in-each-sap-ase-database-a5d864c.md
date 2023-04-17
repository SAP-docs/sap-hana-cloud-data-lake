<!-- loioa5d864cc84f21015b5d1e88185851da5 -->

# Tables in Each SAP ASE Database

Not all SAP Adaptive Server Enterprise system tables are implemented in the data lake Relational Engine system catalog.


<table>
<tr>
<th valign="top">

Table Name



</th>
<th valign="top">

Description



</th>
<th valign="top">

Data?



</th>
<th valign="top">

Supported by Data Lake Relational Engine?



</th>
</tr>
<tr>
<td valign="top">

`sysalternates`



</td>
<td valign="top">

One row for each user mapped to a database user



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syscolumns`



</td>
<td valign="top">

One row for each column in a table or view, and for each parameter in a procedure. In data lake Relational Engine, use the owner name dbo when querying, i.e. dbo.syscolumns.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`syscomments`



</td>
<td valign="top">

One or more rows for each view, rule, default, and procedure, giving SQL definition statement.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`sysconstraints`



</td>
<td valign="top">

One row for each referential and check constraint associated with a table or column.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysdepends`



</td>
<td valign="top">

One row for each procedure, view, or table that is referenced by a procedure, view.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysindexes`



</td>
<td valign="top">

One row for each clustered or nonclustered index, and one row for each table with no indexes, and an additional row for each table containing text or image data. In data lake Relational Engine, use the owner name dbo when querying, i.e. dbo.sysindexes.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`sysiqobjects`



</td>
<td valign="top">

One row for each system table, user table, view, procedure, trigger, event, constraint, domain \(sysdomain\), domain \(sysusertype\), column, and index.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`sysiqvindex`



</td>
<td valign="top">

One row for each non-fp iq index.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`syskeys`



</td>
<td valign="top">

One row for each primary, foreign, or common key; set by user \(not maintained by SAP ASE\).



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syslogs`



</td>
<td valign="top">

Transaction log.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysobjects`



</td>
<td valign="top">

One row for each table, view, procedure, rule, default, log, and \(in tempdb only\) temporary object.



</td>
<td valign="top">

Contains compatible data only



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`sysprocedures`



</td>
<td valign="top">

One row for each view, rule, default, and procedure, giving internal definition.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysprotects`



</td>
<td valign="top">

User permissions information.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysreferences`



</td>
<td valign="top">

One row for each referential integrity constraint declared on a table or column.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`sysroles`



</td>
<td valign="top">

Maps server-wide roles to local database groups.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`syssegments`



</td>
<td valign="top">

One row for each segment \(named collection of disk pieces\).



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`systhresholds`



</td>
<td valign="top">

One row for each threshold defined for the database.



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

`systypes`



</td>
<td valign="top">

One row for each system-supplied and user-defined data type.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

`sysusers`



</td>
<td valign="top">

One row for each user allowed in the database.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Yes



</td>
</tr>
</table>

