<!-- loioa668acaf84f21015bb88a6eb8a856991 -->

# WD\_DELETE\_METHOD Option for Data Lake Relational Engine

Specifies the algorithm used during a delete in a WD index.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa668acaf84f21015bb88a6eb8a856991__iq_refso_1090"/>

## Default

0



<a name="loioa668acaf84f21015bb88a6eb8a856991__iq_refso_1092"/>

## Remarks

WD\_DELETE\_METHOD specifies the algorithm used during a delete operation in a WD index. When this option is set to 0, the delete method is selected by the cost model. The cost model considers the CPU related costs as well as I/O related costs in selecting the appropriate delete algorithm. The cost model takes into account:

-   Rows deleted
-   Index size
-   Width of index data type
-   Cardinality of index data
-   Available temporary cache
-   Machine related I/O and CPU characteristics
-   Available CPUs and threads

