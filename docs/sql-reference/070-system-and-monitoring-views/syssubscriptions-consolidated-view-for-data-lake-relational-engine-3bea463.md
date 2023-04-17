<!-- loio3bea46346c5f1014b224ad518bdb7f6e -->

# SYSSUBSCRIPTIONS Consolidated View for Data Lake Relational Engine

Each row describes a subscription from one user ID \(which must have the REMOTE system privilege\) to one publication.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSSUBSCRIPTIONS"
  as select p.publication_name,u.user_name,s.subscribe_by,s.created,
    s.started
    from SYS.ISYSSUBSCRIPTION as s
      join SYS.ISYSPUBLICATION as p on(p.publication_id = s.publication_id)
      join SYS.ISYSUSER as u on u.user_id = s.user_id
```

