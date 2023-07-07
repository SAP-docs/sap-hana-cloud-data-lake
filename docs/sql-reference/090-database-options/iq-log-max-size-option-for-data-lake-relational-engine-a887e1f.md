<!-- loioa887e1f884f21015ab61e3f24f8a219c -->

# IQ\_LOG\_MAX\_SIZE Option for Data Lake Relational Engine

Sets the maximum size of the point-in-time recovery archive in megabytes.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

0



## Remarks

The point-in-time recovery archive increases in size with each update sequence. The default setting of 0 allows the archive to increase without limit.

**Related Information**  


[IQ\_POINT\_IN\_TIME\_RECOVERY\_LOG\_BACKUP\_INTERVAL Option for Data Lake Relational Engine](iq-point-in-time-recovery-log-backup-interval-option-for-data-lake-relational-engine-a887325.md "Sets a time interval between automatic backups of the point in time recovery logs.")

