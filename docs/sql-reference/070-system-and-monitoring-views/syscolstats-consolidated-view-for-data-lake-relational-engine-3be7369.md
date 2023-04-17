<!-- loio3be7369e6c5f1014a082a74d845643f4 -->

# SYSCOLSTATS Consolidated View for Data Lake Relational Engine

The SYSCOLSTATS view contains the column statistics that are stored as histograms and used by the optimizer.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSCOLSTATS" AS SELECT u.user_name, t.table_name, c.column_name, s.format_id, 
   dateadd(mi, PROPERTY('TimeZoneAdjustment'), s.update_time) as update_time, s.density, s.max_steps, s.actual_steps, 
   s.step_values, s.frequencies , TODATETIMEOFFSET( s.update_time, 0 ) as update_time_utc 
FROM SYS.ISYSCOLSTAT s      
JOIN SYS.ISYSTABCOL c on (s.table_id = c.table_id and s.column_id = c.column_id)     
JOIN SYS.ISYSTAB t on (t.table_id = c.table_id)     
JOIN SYS.ISYSUSER u on (u.user_id = t.creator)
```

