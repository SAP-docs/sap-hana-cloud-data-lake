<!-- loio14c3138ca7ac4e70a0bb3babb3165b28 -->

# SYSPROCS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The SYSPROCS view shows the procedure or function name, the name of its creator and any comments recorded for the procedure or function.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Viewing System Views](remote-execute-usage-examples-for-viewing-system-views-8b235c7.md).
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE\_QUERY procedure.
> 
>     -   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](remote-execute-query-usage-examples-for-viewing-system-views-ada51c0.md).



The tables and columns that make up this view are provided in the following ALTER VIEW statement.

```
ALTER VIEW "SYS"."SYSPROCS"( creator,
  procname,remarks ) 
  AS SELECT u.user_name,p.proc_name,r.remarks
    FROM SYSPROCEDURE AS p
      JOIN ISYSUSER AS u ON u.user_id = p.creator
      LEFT OUTER JOIN ISYSREMARK AS r ON(p.object_id = r.object_id)
```

**Related Information**  


[SYSPROCPARM System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sysprocparm-system-view-for-data-lake-relational-engine-sap-hana-db-managed-80ec5b7.md "Each row in the SYSPROCPARM system view describes one parameter, result set column, or return value of a procedure or function in the database. The underlying system table for this view is ISYSPROCPARM.")

[SYSPROCS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/569e62fd205049ecb6f35968ae512de8.html "The SYSPROCS view shows the procedure or function name, the name of its creator and any comments recorded for the procedure or function.") :arrow_upper_right:

