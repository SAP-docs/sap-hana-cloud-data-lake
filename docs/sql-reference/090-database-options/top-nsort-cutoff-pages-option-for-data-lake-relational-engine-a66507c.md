<!-- loioa66507c784f21015a20e99f6a38ea85c -->

# TOP\_NSORT\_CUTOFF\_PAGES Option for Data Lake Relational Engine

Sets the result size threshold for TOP N algorithm selection.



<a name="loioa66507c784f21015a20e99f6a38ea85c__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa66507c784f21015a20e99f6a38ea85c__iq_refso_1062"/>

## Default

1



<a name="loioa66507c784f21015a20e99f6a38ea85c__iq_refso_1063"/>

## Remarks

TOP\_NSORT\_CUTOFF\_PAGES sets the threshold, measured in pages, where evaluation of a query that contains both a TOP clause and ORDER BY clause switches algorithms from ordered list-based processing to sort-based processing. Ordered list processing performs better in cases where the TOP N value is smaller than the number of result rows. Sort-based processing performs better for large TOP N values.

**Related Information**  


[SELECT Statement for Data Lake Relational Engine](../080-sql-statements/select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

