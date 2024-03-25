<!-- loioa59dae3484f21015bb068d7476af8cf5 -->

# sp\_iqcheckoptions Procedure for Data Lake Relational Engine

For the connected user, sp\_iqcheckoptions displays a list of the current value and the default value of database and server startup options that have been changed from the default.



<a name="loioa59dae3484f21015bb068d7476af8cf5__section_cjs_yvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcheckoptions
```



<a name="loioa59dae3484f21015bb068d7476af8cf5__section_dlg_5jn_zyb"/>

## Parameters

None



<a name="loioa59dae3484f21015bb068d7476af8cf5__section_qnq_syz_mbb"/>

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

User\_name

</td>
<td valign="top">

The name of the user or role for whom the option has been set. At database creation, all options are set for the PUBLIC role. Any option that has been set for a role or user other than PUBLIC is displayed.

</td>
</tr>
<tr>
<td valign="top">

Option\_name

</td>
<td valign="top">

The name of the option.

</td>
</tr>
<tr>
<td valign="top">

Current\_value

</td>
<td valign="top">

The current value of the option.

</td>
</tr>
<tr>
<td valign="top">

Default\_value

</td>
<td valign="top">

The default value of the option.

</td>
</tr>
<tr>
<td valign="top">

Option\_type

</td>
<td valign="top">

“Temporary” for a TEMPORARY option, else “Permanent”.

</td>
</tr>
</table>



<a name="loioa59dae3484f21015bb068d7476af8cf5__iq_refbb_1436"/>

## Remarks

Returns one row for each option that has been changed from the default value. The output is sorted by option name, then by user name.

For the connected user, the sp\_iqcheckoptions stored procedure displays a list of the current value and the default value of database and server startup options that have been changed from the default. sp\_iqcheckoptions considers all data lake Relational Engine and SAP SQL Anywhere database options. Data lake Relational Engine modifies some SAP SQL Anywhere option defaults, and these modified values become the new default values. Unless the new data lake Relational Engine default value is changed again, sp\_iqcheckoptions does not list the option.

When sp\_iqcheckoptions is run, the HDLADMIN user sees all options set on a permanent basis for all roles and users and sees temporary options set for the DBA. Users who are not DBAs see their own temporary options. All users see nondefault server startup options.

The HDLADMIN user sees all options set on a permanent basis for all roles and users, along with temporary options. Users see their own temporary options. All users see nondefault server startup options.



<a name="loioa59dae3484f21015bb068d7476af8cf5__iq_refbb_1434"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa59dae3484f21015bb068d7476af8cf5__iq_refbb_1438"/>

## Examples

This example uses sp\_iqcheckoptions run by user HDLADMIN:

```
CALL  sp_iqcheckoptions;
```


<table>
<tr>
<th valign="top">

User\_name

</th>
<th valign="top">

Option\_name

</th>
<th valign="top">

Current\_value

</th>
<th valign="top">

Default\_value

</th>
<th valign="top">

Option\_type

</th>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

Ansi\_update\_constr

</td>
<td valign="top">

CURSORS

</td>
<td valign="top">

Off

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

PUBLIC

</td>
<td valign="top">

Ansi\_update\_constr

</td>
<td valign="top">

Cursors

</td>
<td valign="top">

Off

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

Checkpoint\_time

</td>
<td valign="top">

20

</td>
<td valign="top">

60

</td>
<td valign="top">

Temporary

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

Connection\_authent

</td>
<td valign="top">

Company=MyComp;

Application=DBTools;Signa

</td>
<td valign="top">

 

</td>
<td valign="top">

Temporary

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

Login\_procedure

</td>
<td valign="top">

HDLADMIN.sp\_iq\_proce

</td>
<td valign="top">

sp\_login\_envir

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

PUBLIC

</td>
<td valign="top">

Login\_procedure

</td>
<td valign="top">

HDLADMIN.sp\_iq\_proce

</td>
<td valign="top">

sp\_login\_envir

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

myrole

</td>
<td valign="top">

Max\_Warnings

</td>
<td valign="top">

9

</td>
<td valign="top">

281474976710655

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

Thread\_count

</td>
<td valign="top">

25

</td>
<td valign="top">

0

</td>
<td valign="top">

Temporary

</td>
</tr>
</table>

This example uses sp\_iqcheckoptions run by user USER1:


<table>
<tr>
<th valign="top">

User\_name

</th>
<th valign="top">

Option\_name

</th>
<th valign="top">

Current\_value

</th>
<th valign="top">

Default\_value

</th>
<th valign="top">

Option\_type

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

Ansi\_update\_constr

</td>
<td valign="top">

CURSORS

</td>
<td valign="top">

Off

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

PUBLIC

</td>
<td valign="top">

Ansi\_update\_constr

</td>
<td valign="top">

Cursors

</td>
<td valign="top">

Off

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

Checkpoint\_time

</td>
<td valign="top">

20

</td>
<td valign="top">

60

</td>
<td valign="top">

Temporary

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

Connection\_authent

</td>
<td valign="top">

Company=MyComp;

Application=DBTools;Signa

</td>
<td valign="top">

 

</td>
<td valign="top">

Temporary

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

Login\_procedure

</td>
<td valign="top">

HDLADMIN.sp\_iq\_proce

</td>
<td valign="top">

sp\_login\_envir

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

PUBLIC

</td>
<td valign="top">

Login\_procedure

</td>
<td valign="top">

HDLADMIN.sp\_iq\_proce

</td>
<td valign="top">

sp\_login\_envir

</td>
<td valign="top">

Permanent

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

Max\_Warnings

</td>
<td valign="top">

55

</td>
<td valign="top">

 

</td>
<td valign="top">

281474976710655Temporary

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

Thread\_count

</td>
<td valign="top">

25

</td>
<td valign="top">

0

</td>
<td valign="top">

Temporary

</td>
</tr>
</table>

