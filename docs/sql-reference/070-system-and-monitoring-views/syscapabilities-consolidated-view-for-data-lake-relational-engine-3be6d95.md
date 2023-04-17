<!-- loio3be6d95b6c5f101490bacd85d8e32485 -->

# SYSCAPABILITIES Consolidated View for Data Lake Relational Engine

Each row in the SYSCAPABILITIES view specifies the status of a capability for a remote database server. This view gets its data from the ISYSCAPABILITY system table.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSCAPABILITIES"
  as select ISYSCAPABILITY.capid,ISYSCAPABILITY.srvid,property('RemoteCapability',ISYSCAPABILITY.capid) as capname,ISYSCAPABILITY.capvalue
    from SYS.ISYSCAPABILITY
```

