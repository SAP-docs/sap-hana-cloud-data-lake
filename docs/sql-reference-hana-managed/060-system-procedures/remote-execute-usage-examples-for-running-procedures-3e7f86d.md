<!-- loio3e7f86d36c3c4335822e2908ee320623 -->

# REMOTE\_EXECUTE Usage Examples for Running Procedures

The process to run a procedure depends on if the procedure returns a results set.



When syntax within the REMOTE\_EXECUTE procedure contains single quotes, they must themselves be enclosed in single quotes. For example, ' '<syntax\>' '.



<a name="loio3e7f86d36c3c4335822e2908ee320623__section_l5j_hml_j4b"/>

## Procedures Producing a Results Set

Procedure sp\_iqtablesize returns information on the size of table T1. To see this information, within the REMOTE\_EXECUTE procedure, you create a data lake Relational Engine view that returns the procedure information as part of a SELECT statement. Since the system procedure allows you to specify the table owner and name, the string must be enclosed in two single quotes.

```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.REMOTE_EXECUTE ('
   CREATE VIEW SIZE_T1 AS SELECT * FROM sp_iqtablesize (' '[/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.T1' ')
');
```

To see the results set of the procedure, execute a query using the system created SAP HANA database virtual table named SIZE\_T1 in the SAP HANA database relational container schema to return all values.

```
SELECT * FROM [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.SIZE_T1;
```

For assistance creating a data lake Relational Engine view, see

-   [Manage Views in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/62b71c7f53f745cd8b5b38338d817fad.html "Create, alter, drop, and list data lake Relational Engine views.") :arrow_upper_right: in *SAP HANA Cloud, Data Lake Administration Guide for Data Lake Relational Engine \(SAP HANA DB-Managed\)*
-   [CREATE VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-4d41128.md) in *SAP HANA Cloud, Data Lake SQL Reference for Data Lake Relational Engine \(SAP HANA DB-Managed\)*



<a name="loio3e7f86d36c3c4335822e2908ee320623__section_wcj_kml_j4b"/>

## Procedures Without a Results Set

Procedure sa\_enable\_auditing\_type enables which events to include in auditing. The procedure has no results set so there is no need to create a data lake Relational Engine view to capture the results. To execute the procedure, within the REMOTE\_EXECUTE procedure, you execute the CALL statement and specify the procedure. Since this system procedure allows you to specify the auditing types to enable, the string must be enclosed in two single quotes.

```
CALL [/pandoc/div/div/horizontalrule/codeblock/span/span
     {""}) SYSHDL (span]_CONTAINER1.REMOTE_EXECUTE ('
   CALL sa_enable_auditing_type (' 'all' ')
');
```

