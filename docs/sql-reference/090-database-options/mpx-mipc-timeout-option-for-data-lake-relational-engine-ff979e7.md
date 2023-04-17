<!-- loioff979e77cda0428792890114e4ec51d4 -->

# MPX\_MIPC\_TIMEOUT Option for Data Lake Relational Engine

Specifies the timeout, in seconds, for MIPC \(multiplex interprocess communication\) calls.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

180 \(seconds\)



## Remarks

During a query, a node sends an MIPC request to another node and waits for results. The MPX\_MIPC\_TIMEOUT prevents indefinite waiting in the event of a network failure or target node deadlock. MIPC requests that exceed the timeout threshold will cancel the query with an error.

