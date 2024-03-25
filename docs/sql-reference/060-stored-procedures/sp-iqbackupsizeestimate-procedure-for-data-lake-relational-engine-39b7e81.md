<!-- loio39b7e81f33504a0a93852bd7cf91fb9d -->

# sp\_iqbackupsizeEstimate Procedure for Data Lake Relational Engine

Displays the estimated backup size \(in bytes\) of backups that are complete, incremental, and incremental since full backup.



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__section_f5t_jrq_tzb"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user.



```
sp_iqbackupsizeEstimate
```



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__section_bf2_xpq_tzb"/>

## Parameters

None



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__section_gv4_xpq_tzb"/>

## Result Set

None



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__iq_refbb_1779"/>

## Remarks

Shows the estimated backup size \(in bytes\) of backups that are complete, incremental, and incremental since full backup. If there is no complete backup, then the size of incremental and incremental since full would be zero.

You cannot run this procedure while an actual data backup is in progress – such an operation returns an error. Example:

```
select * from sp_iqbackupsizeEstimate()
‘Cannot run sp_iqbackupsizeEstimate when data backup is ongoing.’
```



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__iq_refbb_1778"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__iq_refbb_1780"/>

## Examples

This example returns the following output:

```
CALL sp_iqbackupsizeEstimate;
```


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

Full Backup Size:

</td>
<td valign="top">

91291648

</td>
</tr>
<tr>
<td valign="top">

Incremental Since Full Backup Size:

</td>
<td valign="top">

524288

</td>
</tr>
<tr>
<td valign="top">

Incremental Backup Size:

</td>
<td valign="top">

49250304

</td>
</tr>
</table>

