<!-- loio39b7e81f33504a0a93852bd7cf91fb9d -->

# sp\_iqbackupsizeEstimate Procedure for Data Lake Relational Engine

Displays the estimated backup size \(in bytes\) of backups that are complete, incremental, and incremental since full backup.



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__section_w2p_11q_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqbackupsizeEstimate;
```



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__iq_refbb_1779"/>

## Remarks

Shows the estimated backup size \(in bytes\) of backups that are complete, incremental, and incremental since full backup. If there is no complete backup, then the size of incremental and incremental since full would be zero.

You cannot run this procedure while an actual data backup is in progress – such an operation returns an error. Example:

```
select * from sp_iqbackupsizeEstimate();
‘Cannot run sp_iqbackupsizeEstimate when data backup is ongoing.’
```



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__iq_refbb_1778"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loio39b7e81f33504a0a93852bd7cf91fb9d__iq_refbb_1780"/>

## Examples

Normal execution of sp\_iqbackupsizeEstimate returns the following output:

```
select * from sp_iqbackupsizeEstimate();

' Full Backup Size:','299286528'
' Incremental Since Full Backup Size:','3571712'
' Incremental Backup Size:','3571712'
```

