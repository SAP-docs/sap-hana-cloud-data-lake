<!-- loio3bead9b16c5f1014b271fa947ff403ff -->

# SYSTRIGGERS Consolidated View for Data Lake Relational Engine

Each row in the SYSTRIGGERS view describes one trigger in the database. This view also contains triggers that are automatically created for foreign key definitions which have a referential triggered action \(such as ON DELETE CASCADE\).



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSTRIGGERS"( owner,
  trigname,tname,event,trigtime,trigdefn ) 
  as select u.user_name,trig.trigger_name,tab.table_name,
    if trig.event = 'I' then 'INSERT'
    else if trig.event = 'U' then 'UPDATE'
      else if trig.event = 'C' then 'UPDATE'
        else if trig.event = 'D' then 'DELETE'
          else if trig.event = 'A' then 'INSERT,DELETE'
            else if trig.event = 'B' then 'INSERT,UPDATE'
              else if trig.event = 'E' then 'DELETE,UPDATE'
                else 'INSERT,DELETE,UPDATE'
                endif
              endif
            endif
          endif
        endif
      endif
    endif,if trig.trigger_time = 'B' or trig.trigger_time = 'P' then 'BEFORE'
    else if trig.trigger_time = 'A' or trig.trigger_time = 'S' then 'AFTER'
      else if trig.trigger_time = 'R' then 'RESOLVE'
        else 'INSTEAD OF'
        endif
      endif
    endif,trig.trigger_defn
    from SYS.ISYSTRIGGER as trig
      join SYS.ISYSTAB as tab on(tab.table_id = trig.table_id)
      join SYS.ISYSUSER as u on u.user_id = tab.creator where
    trig.foreign_table_id is null
```

