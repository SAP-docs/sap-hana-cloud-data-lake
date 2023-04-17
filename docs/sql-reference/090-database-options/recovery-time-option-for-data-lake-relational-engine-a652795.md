<!-- loioa652795c84f21015a4a2842f5c4c4265 -->

# RECOVERY\_TIME Option for Data Lake Relational Engine

Sets the maximum length of time, in minutes, that the database server takes to recover from system failure.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa652795c84f21015a4a2842f5c4c4265__iq_refso_917"/>

## Default

2



<a name="loioa652795c84f21015a4a2842f5c4c4265__iq_refso_919"/>

## Remarks

This option along with the CHECKPOINT\_TIME option control when checkpoints are done.

A heuristic measures the recovery time based on the operations since the last checkpoint. Thus, the recovery time is not exact.

**Related Information**  


[CHECKPOINT\_TIME Option for Data Lake Relational Engine](checkpoint-time-option-for-data-lake-relational-engine-a62f571.md "Set the maximum length of time, in minutes, that the database server runs without doing a checkpoint.")

