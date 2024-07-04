<!-- loioa5a4d30384f2101589ee88c96ba8bea6 -->

# sp\_iqdbstatistics System Procedure for Data Lake Relational Engine

Reports results of the most recent sp\_iqcheckdb.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__section_j5b_wvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdbstatistics
```



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__section_hrt_f41_vzb"/>

## Parameters

None.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__section_hm3_4bw_c1c"/>

## Result Set

See Examples.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__iq_refbb_1529"/>

## Remarks

Displays the database statistics collected by the most recent execution of sp\_iqcheckdb.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__iq_refbb_1528"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5a4d30384f2101589ee88c96ba8bea6__iq_refbb_1530"/>

## Examples

This example returns the most recent execution of sp\_iqcheckdb 'allocation database':

```
CALL sp_iqdbstatistics;
```

```
            DB Statistics                     Value               Flags
=====================================|===========================|=====
DBCC Allocation Mode Report          |                           |
=====================================|===========================|=====
** DBCC Status                       |No Errors Detected         |
=====================================|===========================|=====
Allocation Summary                   |                           | 
=====================================|===========================|=====
   Blocks Total                      |8404992                    | 
   Blocks in Current Version         |1689407                    | 
   Blocks in All Versions            |1689464                    | 
   Blocks in Use                     |1689464                    | 
   % Blocks in Use                   |20                         | 
                                     |                           |
=====================================|===========================|=====
Allocation Statistics                |                           | 
=====================================|===========================|=====
   Blocks Created in Current TXN     |57                         | 
   Blocks To Drop in Current TXN     |57                         | 
   Marked Logical Blocks             |6640                       | 
   Marked Physical Blocks            |1689464                    | 
   Marked Pages                      |415                        | 
   Blocks in Freelist                |35122639                   | 
   Imaginary Blocks                  |8277503                    | 
   Highest PBN in Use                |9223372036854775807        | 
   Total Free Blocks                 |6725689                    | 
   Usable Free Blocks                |6691021                    | 
   Max Blocks Per Page               |16                         | 
   1  Block Page Count               |301                        | 
   3  Block Page Count               |43                         | 
   16 Block Page Count               |71                         | 
   1  Block Hole Count               |3                          | 
   2  Block Hole Count               |4                          | 
   ...
   14 Block Hole Count               |1                          | 
   16 Block Hole Count               |420338                     | 

Partition Summary
   Database Objects Checked          |7                          |
   Blockmap Page Count               |48                         |
   Blockmaps with Mapped Pages       |3                          |
   Blockmap Identity Count           |4                          |
   Blockmap Max Links                |1                          |
   Bitmap Count                      |7                          |
   Bitmaps with Data                 |3                          |
   Bitmap Physical Block Count       |3                          |
   Bitmap L2 Root Pages              |3                          |
   Bitmap L1 Pages                   |3                          |
   Bitmap Leaf Pages                 |3                          |
   Bitmap Range Slice Count          |6                          |
=====================================|===========================|=====
Connection Statistics                |                           | 
=====================================|===========================|=====
   Sort Records                      |1606                       |
   Sort Sets                         |7                          |
=====================================|===========================|=====
DBCC Indfo
=====================================|===========================|=====
   DBCC Work units Dispatched        |116                        |
   DBCC Work units Completed         |116                        |
   DBCC Buffer Quota                 |3092                       |
   DBCC Per-Thread Buffer Quota      |1546                       |
   Max Blockmap ID found             |26915                      |
   Max Transaction ID found          |1889833                    |
=====================================|===========================|=====
```

