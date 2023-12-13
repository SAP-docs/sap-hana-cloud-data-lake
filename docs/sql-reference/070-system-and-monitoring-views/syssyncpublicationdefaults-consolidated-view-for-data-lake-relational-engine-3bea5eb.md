<!-- loio3bea5eb06c5f101498e9b0aa6a05942b -->

# SYSSYNCPUBLICATIONDEFAULTS Consolidated View for Data Lake Relational Engine

The SYSSYNCPUBLICATIONDEFAULTS view provides the default synchronization settings associated with publications involved in synchronization.



<a name="loio3bea5eb06c5f101498e9b0aa6a05942b__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below.

The server\_connect and option columns display three asterisks \(\*\*\*\) if a value is present in the database and NULL if no value is present.

```
ALTER VIEW "SYS"."SYSSYNCPUBLICATIONDEFAULTS"
  as select "s"."sync_id",
    "p"."publication_name",
    "s"."option",
    "s"."server_connect",
    "s"."server_conn_type"
    from "SYS"."SYSSYNC2" as "s" join "SYS"."SYSPUBLICATION" as "p" on("p"."publication_id" = "s"."publication_id") where
    "s"."site_name" is null;
```

