<!-- loio3e7f86d36c3c4335822e2908ee320623 -->

# REMOTE\_EXECUTE\_QUERY Guidance and Examples for Running Stored Procedures

Use SAP HANA database REMOTE\_EXECUTE\_QUERY when a procedure returns a result set.



You must be connected to an SAP HANA database integrated with data lake Relational Engine \(also referred to as data lake Relational Engine \(SAP HANA DB-Managed\)\) as an SAP HANA database user.

To use REMOTE\_EXECUTE\_QUERY requires:

-   You have the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

REMOTE\_EXECUTE\_QUERY only supports the SELECT statement construct. The SELECT can only include data lake Relational Engine objects, but does support joins.

To generate the query, execute:

```
SELECT <hana_select_criteria> FROM REMOTE_EXECUTE_QUERY ('
   <hana_relational_container_schema>_SOURCE', 
   'SELECT * from <data_lake_procedure_name>');
```

When syntax within REMOTE\_EXECUTE\_QUERY contains quotes, the quotes and text must be escaped with single quotes. '<string\>' becomes ''<string\>''.

For example, to see the result set of the procedure sp\_iqtablesize, execute:

```
SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 'SELECT * FROM sp_iqtablesize (''T1'')');
```

If the procedure references a object in a user-defined relational container schema \(for example, \(SYSHDL\_*<relational\_container\_name\>*\_MYSCHEMA\), you must preface the preface the object name with the relational containerschema name.

For example, to see the result set of the procedure sp\_iqtablesize on table T2 in relational container MYSCHEMA in CONTAINER1, execute:

```
SELECT * FROM REMOTE_EXECUTE_QUERY ('SYSHDL_CONTAINER1_SOURCE', 'SELECT * FROM sp_iqtablesize (''SYSHDL_CONTAINER1_MYSCHEMA.T2'')');
```

