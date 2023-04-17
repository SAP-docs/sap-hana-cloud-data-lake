<!-- loioa877d66984f21015b5d2876b9dadb134 -->

# MAX\_PARTITIONED\_HASH\_MB Option for Data Lake Relational Engine

Sets an upper bound, expressed in megabytes, on the amount of temporary cache space that the optimizer can assume will be available for hash-partitioned hash-based query operators.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

0



## Remarks

When generating a query plan, the IQ optimizer might choose from several algorithms when processing a particular part of a query. These decisions often depend on estimates of the temp cache space that will be required to process that part of the query and on the currently available temp cache.  This option sets an upper bound on estimated temporary space usage for operators that can consider a hash-partitioned hash-based algorithm.

The default value of 0 indicates that there is no hard upper bound, and that therefore optimizer’s choice will be limited only by the current temp cache availability, the current number of active user connections, and the HASH\_PINNABLE\_PERCENT option setting.

Note that this option affects only the optimizer’s algorithm selection decisions, and that the run-time usage may under some circumstances occasionally exceed this limit.

