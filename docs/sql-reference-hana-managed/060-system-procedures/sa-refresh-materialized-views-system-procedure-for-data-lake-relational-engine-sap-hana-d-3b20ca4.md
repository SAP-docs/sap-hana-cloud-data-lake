<!-- loio3b20ca4caa7e4ecb9000e15b95d23644 -->

# sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Initializes all materialized views that are in an uninitialized state.



<a name="loio3b20ca4caa7e4ecb9000e15b95d23644__section_dh4_3db_1yb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sa_refresh_materialized_views( [ <ignore_errors> ] );
```



<a name="loio3b20ca4caa7e4ecb9000e15b95d23644__section_tqq_jyd_srb"/>

## Parameters


<dl>
<dt><b>

*<ignore\_errors\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify whether to return errors during the recompilation. If you specify 0, an error is returned for each view for which column definition failed. If you specify 1, or any value other than 0, no errors are returned. The default is 0.



</dd>
</dl>



<a name="loio3b20ca4caa7e4ecb9000e15b95d23644__section_txq_vsl_zyb"/>

## Results Set

None



<a name="loio3b20ca4caa7e4ecb9000e15b95d23644__section_gtr_2zd_srb"/>

## Remarks

A materialized view may be in an uninitialized state because it has just been created, has just been re-enabled, or the last attempt to initialize or refresh it failed due to an error. The sa\_refresh\_materialized\_views system procedure scans the database for all such materialized views and attempts to initialize them. If the procedure encounters an error initializing a materialized view, it continues on attempting to process the remaining uninitialized views.

You can also use the REFRESH MATERIALIZED VIEW statement to initialize a materialized view.



<a name="loio3b20ca4caa7e4ecb9000e15b95d23644__section_pcw_fy1_1yb"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure.
-   ALTER ANY MATERIALIZED VIEW system privilege



<a name="loio3b20ca4caa7e4ecb9000e15b95d23644__section_ogl_fzd_srb"/>

## Side Effects

None



## Examples

This example uses the sa\_refresh\_materialized\_views system procedure to initialize all materialized views that are in an uninitialized state. Errors are ignored.

```
CALL sa_refresh_materialized_views( 1 );
```

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-sap-hana-db-ma-7897509.md "Returns information about the specified materialized views.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-sap-hana-d-3b20ca4.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sp-iqmaterializedviewstaleness-system-procedure-for-data-lake-relational-engine-sap-hana-0342f57.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-817277b.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_refresh_materialized_views System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/8176eeb16ce21014bfc7bbd9e39afbab.html "Initializes all materialized views that are in an uninitialized state.") :arrow_upper_right:

