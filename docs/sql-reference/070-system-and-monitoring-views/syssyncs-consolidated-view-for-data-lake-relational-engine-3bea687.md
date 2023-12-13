<!-- loio3bea68736c5f1014a03ed8aa39cf1884 -->

# SYSSYNCS Consolidated View for Data Lake Relational Engine

The SYSSYNCS view contains information relating to synchronization.



<a name="loio3bea68736c5f1014a03ed8aa39cf1884__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below. To learn more about a particular table or column, use the links provided beneath the view definition.

The server\_connect and option columns display three asterisks \(\*\*\*\) if a value is present in the database and NULL if no value is present.

The underlying view for this consolidated view is SYSSYNC2.

```
ALTER VIEW "SYS"."SYSSYNCS"
  as select "p"."publication_name","s"."progress","s"."site_name",
    "s"."option",
    "s"."server_connect",
    "s"."server_conn_type","s"."last_download_time",
    "s"."last_upload_time","s"."created","s"."log_sent","s"."generation_number",
    "s"."extended_state"
    from "SYS"."SYSSYNC2" as "s"
      left outer join "SYS"."SYSPUBLICATION" as "p"
      on "p"."publication_id" = "s"."publication_id";
```

