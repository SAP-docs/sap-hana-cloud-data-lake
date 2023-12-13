<!-- loioa65a401984f21015921f928c403787e3 -->

# SWEEPER\_THREADS\_PERCENT Option for Data Lake Relational Engine

Specifies the percentage of data lake Relational Engine threads used to sweep out buffer caches.



<a name="loioa65a401984f21015921f928c403787e3__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa65a401984f21015921f928c403787e3__iq_refso_977"/>

## Default

10



<a name="loioa65a401984f21015921f928c403787e3__iq_refso_979"/>

## Remarks

-   Data lake Relational Engine uses a small percentage of its processing threads as sweeper threads. These sweeper threads clean out dirty pages in the main and temp buffer caches.
-   In the IQ Monitor -cache report, the GDirty column shows the number of times the LRU buffer was grabbed in a “dirty” \(modified\) state.

**Related Information**  


[WASH\_AREA\_BUFFERS\_PERCENT Option for Data Lake Relational Engine](wash-area-buffers-percent-option-for-data-lake-relational-engine-a667a9e.md "Specifies the percentage of the buffer caches above the wash marker.")

