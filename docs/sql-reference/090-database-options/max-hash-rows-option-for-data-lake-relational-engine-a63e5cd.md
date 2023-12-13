<!-- loioa63e5cd884f21015bf7dea5122b66323 -->

# MAX\_HASH\_ROWS Option for Data Lake Relational Engine

Sets the maximum number of rows that the IQ optimizer considers for a hash algorithm.



<a name="loioa63e5cd884f21015bf7dea5122b66323__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63e5cd884f21015bf7dea5122b66323__iq_refso_734"/>

## Default

2,500,000



<a name="loioa63e5cd884f21015bf7dea5122b66323__iq_refso_736"/>

## Remarks

When generating a query plan, the IQ optimizer might have several algorithms \(hash, sort, indexed\) to choose from when processing a particular part of a query. These choices often depend on estimates of the number of rows to process or generate from that part of the query. This option sets an upper boundary for how many estimated rows are considered for a hash algorithm.

If the estimated number of rows entering the join exceeds the value of MAX\_HASH\_ROWS, the optimizer does not consider a hash join.

