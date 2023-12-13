<!-- loioc33cb21ac3b3486a88d30c8ef9053822 -->

# IQ\_SYSTEM\_MAIN\_ALLOCATION\_RATIO Option for Data Lake Relational Engine

Controls the divisor for allocation of space from IQ\_SYSTEM\_MAIN dbspace for use by a multiplex writer.



<a name="loioc33cb21ac3b3486a88d30c8ef9053822__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioc33cb21ac3b3486a88d30c8ef9053822__iq_refso_673"/>

## Default

16



<a name="loioc33cb21ac3b3486a88d30c8ef9053822__iq_refso_675"/>

## Remarks

IQ\_SYSTEM\_MAIN\_ALLOCATION\_RATIO is a divisor for adjusting the requests from multiplex writers to the multiplex coordinator when allocating IQ\_SYSTEM\_MAIN space for use by a writer. The default is 16, meaning that if the requested amount of space from the writer is *<B\>* blocks, then data lake Relational Engine allocates data lake Relational Engine blocks.

**Related Information**  


[IQ\_SYSTEM\_MAIN\_RECOVERY\_THRESHOLD Option for Data Lake Relational Engine](iq-system-main-recovery-threshold-option-for-data-lake-relational-engine-0173dbf.md "Controls the amount of space reserved in IQ_SYSTEM_MAIN that is kept free for recovery operations.")

