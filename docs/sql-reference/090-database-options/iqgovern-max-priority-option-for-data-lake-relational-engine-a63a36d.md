<!-- loioa63a36dd84f21015b5a7cce84258e338 -->

# IQGOVERN\_MAX\_PRIORITY Option for Data Lake Relational Engine

Limits the allowed IQGOVERN\_PRIORITY setting.



<a name="loioa63a36dd84f21015b5a7cce84258e338__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

2



<a name="loioa63a36dd84f21015b5a7cce84258e338__iq_refso_636"/>

## Remarks

Limits the allowed IQGOVERN\_PRIORITY setting, which affects the order in which a user’s queries are queued for execution. In the range of allowed values, 1 indicates high priority, 2 \(the default\) medium priority, and 3 low priority.

**Related Information**  


[IQGOVERN\_PRIORITY Option for Data Lake Relational Engine](iqgovern-priority-option-for-data-lake-relational-engine-a63a661.md "Assigns a priority to each query waiting in the -iqgovern queue.")

[IQGOVERN\_PRIORITY\_TIME Option for Data Lake Relational Engine](iqgovern-priority-time-option-for-data-lake-relational-engine-a63a967.md "Limits the time a high priority query waits in the queue before starting.")

