<!-- loioa63673f584f21015b6dca719ae8410ab -->

# FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine

Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.



<a name="loioa63673f584f21015b6dca719ae8410ab__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa63673f584f21015b6dca719ae8410ab__iq_refso_541"/>

## Default

16 \(MB\)



<a name="loioa63673f584f21015b6dca719ae8410ab__iq_refso_549"/>

## Dependencies

FP\_LOOKUP\_SIZE applies to databases running where FP\_NBIT\_IQ15\_COMPATIBILITY is set to ON. If it is set to OFF, the database engine ignores this option.



<a name="loioa63673f584f21015b6dca719ae8410ab__iq_refso_543"/>

## Remarks

If IQ UNIQUE is ON, FP\_LOOKUP\_SIZE controls the maximum number of lookup pages.

**Related Information**  


[FP\_LOOKUP\_SIZE\_PPM Option for Data Lake Relational Engine](fp-lookup-size-ppm-option-for-data-lake-relational-engine-a636a3a.md "Controls the amount of main buffer cache allocated to FP indexes in data lake Relational Engine 15databases.")

[MINIMIZE\_STORAGE Option for Data Lake Relational Engine](minimize-storage-option-for-data-lake-relational-engine-a64115e.md "Minimizes use of storagespace for newly created columns in data lake Relational Engine databases.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

