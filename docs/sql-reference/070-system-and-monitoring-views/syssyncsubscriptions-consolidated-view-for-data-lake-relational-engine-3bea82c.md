<!-- loio3bea82c96c5f10148ddcd9da28271d70 -->

# SYSSYNCSUBSCRIPTIONS Consolidated View for Data Lake Relational Engine

The SYSSYNCSUBSCRIPTIONS view contains the synchronization settings associated with synchronization subscriptions.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below.

The server\_connect and option columns display three asterisks \(\*\*\*\) if a value is present in the database and NULL if no value is present.

```
ALTER VIEW "SYS"."SYSSYNCSUBSCRIPTIONS"
  as select "s"."sync_id",
    "p"."publication_name",
    "s"."progress",
    "s"."site_name",
    "s"."option",
    "s"."server_connect",
    "s"."server_conn_type",
    "s"."last_download_time",
    "s"."last_upload_time",
    "s"."created",
    "s"."log_sent",
    "s"."generation_number",
    "s"."extended_state"
    from "SYS"."SYSSYNC2" as "s" join "SYS"."SYSPUBLICATION" as "p" on("p"."publication_id" = "s"."publication_id")
    where "s"."publication_id" is not null and
    "s"."site_name" is not null and exists
    (select 1 from "SYS"."SYSSYNCUSERS" as "u"
      where "s"."site_name" = "u"."site_name")
```

