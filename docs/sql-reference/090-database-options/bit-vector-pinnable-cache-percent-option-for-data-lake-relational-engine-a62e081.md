<!-- loioa62e081484f21015a351a621970a27ae -->

# BIT\_VECTOR\_PINNABLE\_CACHE\_PERCENT Option for Data Lake Relational Engine

Maximum percentage of a user’s temp memory that a persistent bit-vector object can pin.



<a name="loioa62e081484f21015a351a621970a27ae__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa62e081484f21015a351a621970a27ae__iq_refso_368"/>

## Default

40%



<a name="loioa62e081484f21015a351a621970a27ae__iq_refso_370"/>

## Remarks

BIT\_VECTOR\_PINNABLE\_CACHE\_PERCENT controls the percentage of a user’s temp memory allocation that any one persistent bit-vector object can pin in memory. It defaults to 40%, and should not generally be changed by users.

**Related Information**  


[HASH\_PINNABLE\_CACHE\_PERCENT Option for Data Lake Relational Engine](hash-pinnable-cache-percent-option-for-data-lake-relational-engine-a637f5a.md "Controls the maximum percentage of a user’s temp memory that a hash object can pin.")

[SORT\_PINNABLE\_CACHE\_PERCENT Option for Data Lake Relational Engine](sort-pinnable-cache-percent-option-for-data-lake-relational-engine-a655979.md "Specifies the maximum percentage of currently available buffers a sort object tries to pin.")

