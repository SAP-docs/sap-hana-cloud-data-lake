<!-- loio3bea8aa26c5f1014ba2d8965d98d284b -->

# SYSSYNCUSERS Consolidated View for Data Lake Relational Engine

A view of synchronization settings associated with synchronization users.



<a name="loio3bea8aa26c5f1014ba2d8965d98d284b__section_v1w_qbq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



The tables and columns that make up this view are provided in the SQL statement below.

The server\_connect and option columns display three asterisks \(\*\*\*\) if a value is present in the database and NULL if no value is present.

```
ALTER VIEW "SYS"."SYSSYNCUSERS"
  as select "SYSSYNC2"."sync_id",
    "SYSSYNC2"."site_name",
    "SYSSYNC2"."option",
    "SYSSYNC2"."server_connect",
    "SYSSYNC2"."server_conn_type"
    from "SYS"."SYSSYNC2" where
    "SYSSYNC2"."publication_id" is null;
```

