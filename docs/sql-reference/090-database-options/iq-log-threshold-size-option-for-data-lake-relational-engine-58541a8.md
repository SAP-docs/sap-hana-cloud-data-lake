<!-- loio58541a8a86224f35aa307db1d9b53e69 -->

# IQ\_LOG\_THRESHOLD\_SIZE Option for Data Lake Relational Engine

Configures the log file threshold for point-in-time recovery. This value is an integer that represents megabytes.



<a name="loio58541a8a86224f35aa307db1d9b53e69__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



## Default

The default value differs depending on database size:

-   Databases smaller than 1 TB – the default threshold size is to 10 percent of dbspace size or 2 GB, whichever is greater.
-   Larger databases – the threshold size is 1 percent of dbspace size.

