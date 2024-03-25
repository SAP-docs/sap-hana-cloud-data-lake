<!-- loioa5a4d30384f2101589ee88c96ba8bea6 -->

# sp\_iqdbstatistics Procedure for Data Lake Relational Engine

Reports results of the most recent sp\_iqcheckdb.



```
sp_iqdbstatistics
```



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__section_hrt_f41_vzb"/>

## Parameters

None



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__section_hm3_4bw_c1c"/>

## Result Set

See Examples.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__iq_refbb_1529"/>

## Remarks

Displays the database statistics collected by the most recent execution of sp\_iqcheckdb.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__iq_refbb_1528"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__iq_refbb_1530"/>

## Examples

This example shows the output from sp\_iqdbstatistics. For this example, the most recent execution of sp\_iqcheckdb was the command sp\_iqcheckdb 'allocation database':

```
            DB Statistics                     Value               Flags
=====================================|===========================|=====
DBCC Allocation Mode Report          |                           |
=====================================|===========================|=====
** DBCC Status                       |Errors Detected            |*****
   DBCC Work units Dispatched        |163                        |
   DBCC Work units Completed         |163                        |
=====================================|===========================|=====
Allocation Summary                   |                           | 
=====================================|===========================|=====
   Blocks Total                      |8192                       | 
   Blocks in Current Version         |4954                       | 
   Blocks in All Versions            |4954                       | 
   Blocks in Use                     |4986                       | 
   % Blocks in Use                   |60                         | 
** Blocks Leaked                     |32                         |*****
                                     |                           |
=====================================|===========================|=====
Allocation Statistics                |                           | 
=====================================|===========================|=====
   Blocks Created in Current TXN     |382                        | 
   Blocks To Drop in Current TXN     |382                        | 
   Marked Logical Blocks             |8064                       | 
   Marked Physical Blocks            |4954                       | 
   Marked Pages                      |504                        | 
   Blocks in Freelist                |126553                     | 
   Imaginary Blocks                  |121567                     | 
   Highest PBN in Use                |5432                       | 
** 1st Unowned PBN                   |452                        |*****
   Total Free Blocks                 |3206                       | 
   Usable Free Blocks                |3125                       | 
   % Free Space Fragmented           |2                          |
   Max Blocks Per Page               |16                         | 
   1  Block Page Count               |97                         | 
   3  Block Page Count               |153                        | 
   4  Block Page Count               |14                         | 
   ...
   9  Block Hole Count               |2                          | 
   16 Block Hole Count               |194                        | 
                                     |                           | 
   Database Objects Checked          |1                          | 
   B-Array Count                     |1                          | 
   Blockmap Identity Count           |1                          | 
=====================================|===========================|=====
Connection Statistics                |                           | 
=====================================|===========================|=====
```

