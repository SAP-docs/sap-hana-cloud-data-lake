<!-- loioa62ef8de84f2101599bb9ae14767ff72 -->

# CACHE\_PARTITIONS Option for Data Lake Relational Engine

Sets the number of partitions to be used for the main and temporary buffer caches.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

0



<a name="loioa62ef8de84f2101599bb9ae14767ff72__iq_refso_392"/>

## Remarks

This value applies to both the main and temp buffer caches.

The number of partitions does not affect other buffer cache settings. It also does not affect statistics collected by the IQ monitor; statistics for all partitions are rolled up and reported as a single value.

