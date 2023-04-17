<!-- loio3bea56376c5f1014a904b578fa72d551 -->

# SYSSYNC2 Consolidated View for Data Lake Relational Engine

The SYSSYNC2 view provides public access to the data found in the SYSSYNC system view \(information related to synchronization\) without exposing potentially sensitive data.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular column, use the links provided beneath the view definition.

The server\_connect and option columns display three asterisks \(\*\*\*\) if a value is present in the database and NULL if no value is present.

```
ALTER VIEW "SYS"."SYSSYNC2"
  as select "ISYSSYNC"."sync_id",
    "ISYSSYNC"."type",
    "ISYSSYNC"."publication_id",
    "ISYSSYNC"."progress",
    "ISYSSYNC"."site_name",
    if "ISYSSYNC"."option" is null then null else '***' endif as "option",
    if "ISYSSYNC"."server_connect" is null then null else '***' endif as "server_connect",
    "ISYSSYNC"."server_conn_type",
    "ISYSSYNC"."last_download_time",
    "ISYSSYNC"."last_upload_time",
    "ISYSSYNC"."created",
    "ISYSSYNC"."log_sent",
    "ISYSSYNC"."generation_number",
    "ISYSSYNC"."extended_state",
    "ISYSSYNC"."script_version",
    "ISYSSYNC"."subscription_name",
    "ISYSSYNC"."server_protocol"
    from "SYS"."ISYSSYNC"
```

