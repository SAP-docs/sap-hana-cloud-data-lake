<!-- loioa63a661e84f210158ee2c8e1602d1eb4 -->

# IQGOVERN\_PRIORITY Option for Data Lake Relational Engine

Assigns a priority to each query waiting in the -iqgovern queue.



<a name="loioa63a661e84f210158ee2c8e1602d1eb4__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

2



<a name="loioa63a661e84f210158ee2c8e1602d1eb4__iq_refso_640"/>

## Remarks

Assigns a value that determines the order in which a user’s queries are queued for execution. In the range of allowed values, 1 indicates high priority, 2 \(the default\) medium priority, and 3 low priority. Queries with a lower priority will not run until all higher priority queries have executed.

**Related Information**  


[IQGOVERN\_MAX\_PRIORITY Option for Data Lake Relational Engine](iqgovern-max-priority-option-for-data-lake-relational-engine-a63a36d.md "Limits the allowed IQGOVERN_PRIORITY setting.")

[IQGOVERN\_PRIORITY\_TIME Option for Data Lake Relational Engine](iqgovern-priority-time-option-for-data-lake-relational-engine-a63a967.md "Limits the time a high priority query waits in the queue before starting.")

