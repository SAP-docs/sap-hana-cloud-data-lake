<!-- loioa667a9e684f21015a87fa925d061b800 -->

# WASH\_AREA\_BUFFERS\_PERCENT Option for Data Lake Relational Engine

Specifies the percentage of the buffer caches above the wash marker.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa667a9e684f21015a87fa925d061b800__iq_refso_1082"/>

## Default

20



<a name="loioa667a9e684f21015a87fa925d061b800__iq_refso_1084"/>

## Remarks

Data lake Relational Engine buffer caches are organized as a long MRU/LRU chain. The area above the wash marker is used to sweep out \(that is, write\) dirty pages to disk.

**Related Information**  


[SWEEPER\_THREADS\_PERCENT Option for Data Lake Relational Engine](sweeper-threads-percent-option-for-data-lake-relational-engine-a65a401.md "Specifies the percentage of data lake Relational Engine threads used to sweep out buffer caches.")

