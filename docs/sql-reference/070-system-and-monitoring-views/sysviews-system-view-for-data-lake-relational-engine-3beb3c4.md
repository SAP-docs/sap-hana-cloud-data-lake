<!-- loio3beb3c476c5f10149333ff887924c019 -->

# SYSVIEWS System View for Data Lake Relational Engine

Each row of the SYS.SYSVIEWS view describes one view, including its view definition.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the following SQL statement.

```
ALTER VIEW "SYS"."SYSVIEWS"( vcreator,
  viewname,viewtext ) 
  AS SELECT u.user_name,t.table_name,v.view_def
    FROM SYS.SYSTAB as t
      JOIN SYS.ISYSVIEW AS v ON(t.object_id = v.view_object_id)
      JOIN SYS.ISYSUSER AS u ON(u.user_id = t.creator)
```

**Related Information**  


[SYSVIEWS System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/1f4dedee333d46d1bd4c31ea6c2a440e.html "Each row of the SYS.SYSVIEWS view describes one view, including its view definition.") :arrow_upper_right:

