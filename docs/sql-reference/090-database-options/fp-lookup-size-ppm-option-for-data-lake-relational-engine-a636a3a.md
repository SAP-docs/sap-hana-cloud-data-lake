<!-- loioa636a3a184f21015bd0190caa12fa1a2 -->

# FP\_LOOKUP\_SIZE\_PPM Option for Data Lake Relational Engine

Controls the amount of main buffer cache allocated to FP indexes in data lake Relational Engine 15databases.



<a name="loioa636a3a184f21015bd0190caa12fa1a2__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa636a3a184f21015bd0190caa12fa1a2__iq_refso_548"/>

## Default

2500



## Dependencies

FP\_LOOKUP\_SIZE\_PPM applies to databases running where FP\_NBIT\_IQ15\_COMPATIBILITY is set to ON. If set to OFF, data lake Relational Engine ignores this option.



<a name="loioa636a3a184f21015bd0190caa12fa1a2__iq_refso_550"/>

## Remarks

If FP\_NBIT\_IQ15\_COMPATIBILITY is ON, FP\_LOOKUP\_SIZE\_PPM controls the maximum number of lookup pages and restricts this number to a parts-per-million value of main memory, that is, the value of FP\_LOOKUP\_SIZE\_PPM \* size of main memory / 1,000,000, where the size of main memory is specified by the -iqmc server startup parameter.

**Related Information**  


[FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine](fp-lookup-size-optionfor-data-lake-relational-engine-a63673f.md "Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.")

[MINIMIZE\_STORAGE Option for Data Lake Relational Engine](minimize-storage-option-for-data-lake-relational-engine-a64115e.md "Minimizes use of storagespace for newly created columns in data lake Relational Engine databases.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

