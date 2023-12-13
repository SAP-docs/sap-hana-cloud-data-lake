<!-- loioa4d825ce84f21015afff83e9dabeec9a -->

# MPX\_MAX\_CONNECTION\_POOL\_SIZE Option for Data Lake Relational Engine

Maximum number of connections allowed in the connection pool on a worker node.



<a name="loioa4d825ce84f21015afff83e9dabeec9a__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa4d825ce84f21015afff83e9dabeec9a__iq_iqmpx_211"/>

## Default

The default value varies based on the size of the worker node:

-   10 - small nodes
-   15 - medium nodes
-   50 - large, xlarge, 2xlarge, and 3xlarge nodes



## Remarks

INC connections are inter-server connections between worker nodes and the coordinator node. An INC connection is associated with each user connection on a worker doing a DDL or read-write operation. The connection is active until that command commits or rolls back; it then returns to the pool. If these transactions are short lived, then the default setting of MPX\_MAX\_CONNECTION\_POOL\_SIZE suffices for many user connections running DDL or RW operations. If many concurrent connections run DDL or read-write operations, or the transactions take a long time, increase the value of MPX\_MAX\_CONNECTION\_POOL\_SIZE. For example, increase the value when many user connections do concurrent loads without committing.

Exceeding MPX\_MAX\_CONNECTION\_POOL\_SIZE returns the following message:

```
SQL Anywhere Error -1004000: The number of connections in 
the connection pool have exceeded the upper limit.
```

