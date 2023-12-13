<!-- loio0173dbf933824016843aeab50948409d -->

# IQ\_SYSTEM\_MAIN\_RECOVERY\_THRESHOLD Option for Data Lake Relational Engine

Controls the amount of space reserved in IQ\_SYSTEM\_MAIN that is kept free for recovery operations.



<a name="loio0173dbf933824016843aeab50948409d__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loio0173dbf933824016843aeab50948409d__iq_refso_673"/>

## Default

1 percent



<a name="loio0173dbf933824016843aeab50948409d__iq_refso_675"/>

## Remarks

Data lake Relational Engine reserves the percentage of the IQ\_SYSTEM\_MAIN dbspace specified by the IQ\_SYSTEM\_MAIN\_RECOVERY\_THRESHOLD to use during database recovery after a server failure.

**Related Information**  


[IQ\_SYSTEM\_MAIN\_ALLOCATION\_RATIO Option for Data Lake Relational Engine](iq-system-main-allocation-ratio-option-for-data-lake-relational-engine-c33cb21.md "Controls the divisor for allocation of space from IQ_SYSTEM_MAIN dbspace for use by a multiplex writer.")

