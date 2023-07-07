<!-- loioa62e965884f21015a56fc667d1720a8f -->

# BT\_PREFETCH\_SIZE Option for Data Lake Relational Engine

Restricts the size of the read-ahead buffer for the High\_Group B-tree.



> ### Restriction:  
> This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa62e965884f21015a56fc667d1720a8f__iq_refso_380"/>

## Default

NULL



<a name="loioa62e965884f21015a56fc667d1720a8f__iq_refso_382"/>

## Remarks

Setting the value to 0 disables B-tree prefetch.

B-tree prefetch is activated by default for any sequential access to the High\_Group index such as INSERT, large DELETE, range predicates, and DBCC \(Database Consistency Checker\) commands.

**Related Information**  


[GARRAY\_INSERT\_PREFETCH\_SIZE Option for Data Lake Relational Engine](garray-insert-prefetch-size-option-for-data-lake-relational-engine-a63762f.md "Specifies number of pages used for prefetch.")

[GARRAY\_RO\_PREFETCH\_SIZE Option for Data Lake Relational Engine](garray-ro-prefetch-size-option-for-data-lake-relational-engine-a637c5e.md "Specifies number of pages used for prefetch.")

[PREFETCH\_GARRAY\_PERCENT Option for Data Lake Relational Engine](prefetch-garray-percent-option-for-data-lake-relational-engine-a64ab57.md "Specifies the percent of prefetch resources designated for performing all DML operations (insert, update, delete, query) on HG indexes.")

