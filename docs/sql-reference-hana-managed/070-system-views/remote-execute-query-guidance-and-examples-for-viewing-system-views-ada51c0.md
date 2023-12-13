<!-- loioada51c0074354a5f99b60c14cffb653c -->

# REMOTE\_EXECUTE\_QUERY Guidance and Examples for Viewing System Views

Use SAP HANA database REMOTE\_EXECUTE\_QUERY to view data lake Relational Engine system views.



You must be connected to an SAP HANA database integrated with data lake Relational Engine \(also referred to as data lake Relational Engine \(SAP HANA DB-Managed\)\) as an SAP HANA database user.

To use REMOTE\_EXECUTE\_QUERY requires:

-   You have the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.



REMOTE\_EXECUTE\_QUERY only supports the SELECT statement construct. The SELECT can only include data lake Relational Engine objects, but does support joins.

To generate the query, execute:

```
SELECT <hana_select_criteria> FROM REMOTE_EXECUTE_QUERY ('
   <hana_relational_container_schema>_SOURCE', 
   'SELECT <data_lake_system_view_name>');
```

For example, to query the data lake Relational Engine SYSIQTABCOL system view, execute:

```
SELECT <*> FROM REMOTE_EXECUTE_QUERY (
   'SYSHDL_CONTAINER1_SOURCE', 
   'SELECT * FROM SYSIQTABCOL');
```

When syntax within REMOTE\_EXECUTE\_QUERY contains quotes, the quotes and text must be escaped with single quotes. '<string\>' becomes ''<string\>''.

