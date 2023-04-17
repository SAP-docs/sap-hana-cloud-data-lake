<!-- loio569e62fd205049ecb6f35968ae512de8 -->

# SYSPROCS System View for Data Lake Relational Engine

The SYSPROCS view shows the procedure or function name, the name of its creator and any comments recorded for the procedure or function.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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


[SYSPROCPARM System View for Data Lake Relational Engine](sysprocparm-system-view-for-data-lake-relational-engine-3be9842.md "Each row in the SYSPROCPARM system view describes one parameter, result set column, or return value of a procedure or function in the database. The underlying system table for this view is ISYSPROCPARM.")

[SYSPROCS System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/14c3138ca7ac4e70a0bb3babb3165b28.html "The SYSPROCS view shows the procedure or function name, the name of its creator and any comments recorded for the procedure or function.") :arrow_upper_right:

