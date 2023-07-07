<!-- loioada51c0074354a5f99b60c14cffb653c -->

# REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views

The REMOTE\_EXECUTE\_QUERY procedure lets you execute SELECT queries on data lake Relational Engine system views without using an SAP HANA database virtual table in the query.



The REMOTE\_EXECUTE\_QUERY only supports the SELECT statement construct. The SELECT can only include data lake Relational Engine objects, but does support joins.

To generate the query, execute:

```
SELECT <hana_select_criteria> FROM REMOTE_EXECUTE_QUERY ('
   SYSHDL_<relational_container_name>_SOURCE', 
   'SELECT <data_lake_select_criteria>');
```



For example, to query the data lake Relational Engine SYSIQTABCOL system view, execute:

```
SELECT <*> FROM REMOTE_EXECUTE_QUERY (
   'SYSHDL_CONTAINER1_SOURCE', 
   'SELECT * FROM SYSIQTABCOL');
```

