<!-- loioa449021984f210158379d2988674516d -->

# CACHE\_AFFINITY\_PERCENT Option for Data Lake Relational Engine

The maximum percentage of main buffer cache to use for affinity. Non-affinity data can use this area if insufficient affinity data exists.



<a name="loioa449021984f210158379d2988674516d__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

75%



## Remarks

This option defines the percentage of the buffer cache used for affinitized data buffers. Data lake Relational Engine buffer caches are organized as a long MRU/LRU chain. Non-affinitized data buffers are put into the chain after affinitized buffers when this percentage is non-zero, so that affinitized data stay in the cache longer than non-affinitized data. If there are insufficient affinitized data buffers to fill this entire percentage, non-affinitized data may consume the remainder.

