<!-- loioa638554984f210159bbf86926740c08b -->

# HG\_DELETE\_METHOD Option for Data Lake Relational Engine

Specifies the algorithm used during a delete in a HG index.



<a name="loioa638554984f210159bbf86926740c08b__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa638554984f210159bbf86926740c08b__iq_refso_587"/>

## Default

0



<a name="loioa638554984f210159bbf86926740c08b__iq_refso_589"/>

## Remarks

This option chooses the algorithm used by the HG index during a delete operation. The cost model considers both CPU- and I/O-related in selecting the appropriate delete algorithm. The cost model takes the following into account:

-   Rows deleted
-   Index size
-   Width of index data type
-   Cardinality of index data
-   Available temporary cache
-   Machine related I/O and CPU characteristics
-   Available CPUs and threads
-   Referential integrity costs

