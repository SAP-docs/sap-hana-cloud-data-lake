<!-- loioa5b2408984f21015a45eae4a5eaef8e7 -->

# sp\_iqprocedure System Procedure for Data Lake Relational Engine

Displays information about system and user-defined procedures.



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqprocedure [ <proc-name> ], [ <proc-owner> ], [ <proc-type> ]
```



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__sp_iqprocedure_parm1"/>

## Parameters


<dl>
<dt><b>

*<proc-name\>*

</b></dt>
<dd>

\(Optional\) The name of the procedure.



</dd><dt><b>

*<proc-owner\>*

</b></dt>
<dd>

\(Optional\) The owner of the procedure.



</dd><dt><b>

*<proc-type\>*

</b></dt>
<dd>

\(Optional\) The type of procedure. Allowed values are:

-   SYSTEM – displays information about system procedures \(procedures owned by user SYS or dbo\) only
-   ALL – displays information about user and system procedures
-   Any other value – displays information about user procedures



</dd>
</dl>



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__sp_iqprocedure_returns1"/>

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

proc\_name

</td>
<td valign="top">

The name of the procedure.

</td>
</tr>
<tr>
<td valign="top">

proc\_owner

</td>
<td valign="top">

The owner of the procedure.

</td>
</tr>
<tr>
<td valign="top">

proc\_defn

</td>
<td valign="top">

The command used to create the procedure. For hidden procedures, the keyword 'HIDDEN' is displayed.

</td>
</tr>
<tr>
<td valign="top">

replicate

</td>
<td valign="top">

Displays Y if the procedure is a primary data source in a Replication Server installation; N if not.

</td>
</tr>
<tr>
<td valign="top">

srvid

</td>
<td valign="top">

Indicates the remote server, if the procedure is on a remote database server.

</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

A comment string

</td>
</tr>
</table>



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__sp_iqprocedure_remarks1"/>

## Remarks

The sp\_iqprocedure procedure can be invoked without any parameters. If no parameters are specified, only information about user-defined procedures \(procedures not owned by dbo or SYS\) is displayed by default.

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, `sp_iqprocedure NULL, NULL, SYSTEM` and `sp_iqprocedure NULL, user1`.


<table>
<tr>
<th valign="top">

Syntax

</th>
<th valign="top">

Output

</th>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure

</td>
<td valign="top">

Displays information about all procedures in the database not owned by dbo or SYS.

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure sp\_test

</td>
<td valign="top">

Displays information about the procedure sp\_test.

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure non\_existing\_proc

</td>
<td valign="top">

No rows returned, as the procedure non\_existing\_proc does not exist.

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure NULL, HDLADMIN

</td>
<td valign="top">

Displays information about all procedures owned by HDLADMIN.

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure sp\_test, HDLADMIN

</td>
<td valign="top">

Displays information about the procedure sp\_test owned by HDLADMIN.

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure sp\_iqtable

</td>
<td valign="top">

The procedure sp\_iqtable is not a system procedure. If there is no user-defined procedure also named sp\_iqtable, no rows are returned \(by default only user-defined procedures are returned\).

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure sp\_iqtable, dbo

</td>
<td valign="top">

No rows returned, as the procedure sp\_iqtable is not a user procedure \(by default only user procedures returned\).

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure NULL, NULL, SYSTEM

</td>
<td valign="top">

Displays information about all system procedures \(owned by dbo or SYS\).

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure sp\_iqtable, NULL, SYSTEM

</td>
<td valign="top">

Displays information about the system procedure sp\_iqtable.

</td>
</tr>
<tr>
<td valign="top">

sp\_iqprocedure sp\_iqtable, dbo, ALL

</td>
<td valign="top">

Displays information about the system procedure sp\_iqtable owned by dbo.

</td>
</tr>
</table>

The sp\_iqprocedure stored procedure displays information about procedures in a database. If you specify one or more parameters, the result is filtered by the specified parameters. For example, if *<proc-name\>* is specified, only information about the specified procedure is displayed. If *<proc-owner\>* is specified, `sp_iqprocedure` returns only information about procedures owned by the specified owner. If no parameters are specified, sp\_iqprocedure displays information about all the user-defined procedures in the database.



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__sp_iqprocedure_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__sp_iqprocedure_sideeffects1"/>

## Side Effects

None.



<a name="loioa5b2408984f21015a45eae4a5eaef8e7__sp_iqprocedure_examples1"/>

## Examples

This example returns information about all user-defined procedures.

```
CALL sp_iqprocedure;
```


<table>
<tr>
<th valign="top">

proc\_name

</th>
<th valign="top">

proc\_owner

</th>
<th valign="top">

proc\_defn

</th>
<th valign="top">

replicate

</th>
<th valign="top">

srvid

</th>
<th valign="top">

remarks

</th>
</tr>
<tr>
<td valign="top">

Proc1

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

CREATE PROCEDURE "HDLADMIN"."Proc1"\(\)…

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

Proc2

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

CREATE PROCEDURE "HDLADMIN"."Proc2"\(\)…

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

Proc3

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

CREATE PROCEDURE "HDLADMIN"."Proc3"\(\)…

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

my\_proc1

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

CREATE PROCEDURE "HDLADMIN"."my\_proc1…

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

my\_proc2

</td>
<td valign="top">

USER1

</td>
<td valign="top">

CREATE PROCEDURE "USER1"."my\_proc2"\(…

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

my\_proc3

</td>
<td valign="top">

USER1

</td>
<td valign="top">

CREATE PROCEDURE "USER1"."my\_proc3"\(…

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

This example returns information about all procedures owned by user USER1:

```
CALL sp_iqprocedure (NULL, 'USER1');
```

