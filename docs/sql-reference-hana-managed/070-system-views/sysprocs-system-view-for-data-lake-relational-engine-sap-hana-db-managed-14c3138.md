<!-- loio14c3138ca7ac4e70a0bb3babb3165b28 -->

# SYSPROCS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The SYSPROCS view shows the procedure or function name, the name of its creator and any comments recorded for the procedure or function.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.




The tables and columns that make up this view are provided in the following ALTER VIEW statement.

```
ALTER VIEW "SYS"."SYSPROCS"( creator,
  procname,remarks ) 
  AS SELECT u.user_name,p.proc_name,r.remarks
    FROM SYSPROCEDURE AS p
      JOIN ISYSUSER AS u ON u.user_id = p.creator
      LEFT OUTER JOIN ISYSREMARK AS r ON(p.object_id = r.object_id);
```



<a name="loio14c3138ca7ac4e70a0bb3babb3165b28__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSPROCPARM System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sysprocparm-system-view-for-data-lake-relational-engine-sap-hana-db-managed-80ec5b7.md "Each row in the SYSPROCPARM system view describes one parameter, result set column, or return value of a procedure or function in the database. The underlying system table for this view is ISYSPROCPARM.")

[SYSPROCS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/569e62fd205049ecb6f35968ae512de8.html "The SYSPROCS view shows the procedure or function name, the name of its creator and any comments recorded for the procedure or function.") :arrow_upper_right:

