<!-- loioa63d330e84f21015acd7fd3f32fa64d5 -->

# MAIN\_RESERVED\_DBSPACE\_MB Option for Data Lake Relational Engine

Controls the amount of space data lake Relational Engine reserves in the IQ main store.



<a name="loioa63d330e84f21015acd7fd3f32fa64d5__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63d330e84f21015acd7fd3f32fa64d5__iq_refso_707"/>

## Default

200



<a name="loioa63d330e84f21015acd7fd3f32fa64d5__iq_refso_709"/>

## Remarks

MAIN\_RESERVED\_DBSPACE\_MB controls the amount of space data lake Relational Engine sets aside in the IQ main store for certain small but critical data structures used during release savepoint, commit, and checkpoint operations.

Reserved space size is calculated as a maximum of 50 percent and a minimum of 1 percent of the last read-write file in IQ\_SYSTEM\_MAIN.

Data lake Relational Engine ignores the MAIN\_RESERVED\_DBSPACE\_MB option if the actual dbspace size is less than twice the size of the MAIN\_RESERVED\_DBSPACE\_MB value. In dbspaces less than 100 MB, half the usable space may be reserved.

