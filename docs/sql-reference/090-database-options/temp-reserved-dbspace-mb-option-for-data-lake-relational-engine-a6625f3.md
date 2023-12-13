<!-- loioa6625f3384f21015958ed54e3af571e1 -->

# TEMP\_RESERVED\_DBSPACE\_MB Option for Data Lake Relational Engine

Controls the amount of space data lake Relational Engine reserves in the temporary IQ store.



<a name="loioa6625f3384f21015958ed54e3af571e1__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa6625f3384f21015958ed54e3af571e1__iq_refso_1043"/>

## Default

200. Data lake Relational Engine actually reserves a maximum of 50% and a minimum of 1 percent of the last read-write file in IQ\_SYSTEM\_TEMP



<a name="loioa6625f3384f21015958ed54e3af571e1__iq_refso_1045"/>

## Remarks

TEMP\_RESERVED\_DBSPACE\_MB lets you control the amount of space data lake Relational Engine sets aside in your temporary IQ store for certain small but critical data structures used during release savepoint, commit, and checkpoint operations. The larger your IQ page size and number of concurrent connections, the more reserved space you need.

