<!-- loioa25b5e6f84f21015bad59eda122ceed0 -->

# MPX\_LIVENESS\_TIMEOUT Option for Data Lake Relational Engine

Time, in seconds, before a heartbeat on a secondary server declares the coordinator offline if the heartbeat fails to reconnect to the coordinator after the first disconnect. This option also determines how long the coordinator keeps a global transaction in a suspended state.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

3600 seconds \(1 hour\)



## Remarks

If a writer fails to resume a suspended transaction within the MPX\_LIVENESS\_TIMEOUT period, the transaction can no longer commit, and the user should roll back the transaction. The coordinator keeps a global transaction in a suspended state for a period of 2 \* MPX\_LIVENESS\_TIMEOUT. If the corresponding writer fails to resume the transaction before the 2 \* MPX\_LIVENESS\_TIMEOUT period, the coordinator rolls back the suspended transaction.

