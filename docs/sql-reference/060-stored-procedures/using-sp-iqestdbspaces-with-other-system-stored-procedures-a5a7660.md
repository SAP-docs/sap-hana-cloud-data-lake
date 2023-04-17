<!-- loioa5a7660384f21015b843ab4916c7a6e0 -->

# Using sp\_iqestdbspaces With Other System Stored Procedures

You need to run two stored procedures to provide the *<db\_size\_in\_bytes\>* parameter needed by sp\_iqestdbspaces.



## Context

Results of sp\_iqestdbspaces are only estimates, based on the average size of an index. The actual size depends on the data stored in the tables, particularly on how much variation there is in the data.

SAP strongly recommends that you create the spare dbspace segments, because you can delete them later if they are unused.



## Procedure

1.  Select one of the suggested index sizes for each pair of tables.

2.  Total the index sizes you selected for all tables.

3.  Run sp\_iqestspace for all tables.

4.  Total all of the RAW DATA index sizes returned by sp\_iqestspace.

5.  Add the total from step 3 to the total from step 5 to determine total index size.

6.  Use the total index size calculated in step 6 as the *<db\_size\_in\_bytes\>* parameter in sp\_iqestdbspaces.


