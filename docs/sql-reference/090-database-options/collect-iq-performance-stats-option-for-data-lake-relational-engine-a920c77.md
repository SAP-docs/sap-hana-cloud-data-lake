<!-- loioa920c77d22574357b8426dd3b69ff32f -->

# COLLECT\_IQ\_PERFORMANCE\_STATS Option for Data Lake Relational Engine

Enables statement performance monitoring for data lake Relational Engine queries.



<a name="loioa920c77d22574357b8426dd3b69ff32f__section_rv2_mvs_swb"/>

## Usage

This data lake Relational Engine database option is set by the system and cannot be changed.



<a name="loioa920c77d22574357b8426dd3b69ff32f__section_tmn_mgf_lbb"/>

## Default

OFF



<a name="loioa920c77d22574357b8426dd3b69ff32f__section_c2b_x2k_kbb"/>

## Remarks

To control statistics collection based on query execution time, you can use the QUERY\_PLAN\_MIN\_TIME option. Statistics for any query having an execution time *less* than the value of QUERY\_PLAN\_MIN\_TIME are not recorded.

**Related Information**  


[Monitoring Statement Performance in Data Lake Relational Engine](https://help.sap.com/viewer/a8982cc084f21015a7b4b7fcdeb0953d/2024_1_QRC/en-US/a50746e62c2248c2a66f34c8e34fb722.html "The statement performance monitoring feature is not an exhaustive, complete audit of slow SQL statements (queries), but it is a useful tool for providing an approximation, or high-level summary, of query workload. Statement performance monitoring flags certain outlier statements with execution times exceeding an established baseline.") :arrow_upper_right:

[QUERY\_PLAN\_MIN\_TIME Option for Data Lake Relational Engine](query-plan-min-time-option-for-data-lake-relational-engine-a31267e.md "Specifies a threshold for query execution. The post-query plan is generated only if the query execution time exceeds the threshold.")

[GTSYSPERFCACHEPLAN System View for Data Lake Relational Engine](../070-system-and-monitoring-views/gtsysperfcacheplan-system-view-for-data-lake-relational-engine-6df8e7a.md "Each row in the GTSYSPERFCACHEPLAN system view contains a graphical plan string for an execution plan of the specified statement.")

[GTSYSPERFCACHESTMT System View for Data Lake Relational Engine](../070-system-and-monitoring-views/gtsysperfcachestmt-system-view-for-data-lake-relational-engine-7c163a0.md "Each row in the GTSYSPERFCACHESTMT system view represents SQL text for a statement with the constants removed.")

