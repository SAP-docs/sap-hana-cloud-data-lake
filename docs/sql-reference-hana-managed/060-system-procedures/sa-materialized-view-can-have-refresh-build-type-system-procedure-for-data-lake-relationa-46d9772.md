<!-- loio46d97724fd354bb68d1c4081bd2576b0 -->

# sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Checks whether the materialized view supports the specified refresh and build type properties.



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_materialized_view_can_have_refresh_build_type(
   '<refresh-type>', '<build-type>', 
   '<view_name>', '<schema_name>' )
```



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_vsv_nhd_bwb"/>

## Parameters


<dl>
<dt><b>

*<refresh\_type\>* 

</b></dt>
<dd>

Specifies the refresh type of the materialized view. Valid values are:

-   I = IMMEDIATE
-   A = AUTO
-   M = MANUAL



</dd><dt><b>

*<build\_type\>* 

</b></dt>
<dd>

Specifies the build type of the materialized view. Valid values are:

-   I = INCREMENTAL
-   F = FULL



</dd><dt><b>

*<owner\_name\>* | *<schema\_name\>*

</b></dt>
<dd>

Specifies the owner of the materialized



</dd>
</dl>



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_m1k_4hd_bwb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

SQLStateVal

</td>
<td valign="top">

CHAR\(6\)

</td>
<td valign="top">

The SQLSTATE returned.

</td>
</tr>
<tr>
<td valign="top">

ErrorMessage

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The error message corresponding to the SQLSTATE.

</td>
</tr>
</table>



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_s2g_phd_bwb"/>

## Remarks

This procedure returns a table with a list of errors that prevents the specified materialized view from being altered with the specified *<refresh\_type\>* and *<build\_type\>* values.



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_lqh_ky1_1yb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using REMOTE\_EXECUTE\_QUERY:

</b></dt>
<dd>

Requires the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Guidance and Examples for Running Stored Procedures](remote-execute-query-guidance-and-examples-for-running-stored-procedures-3e7f86d.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires EXECUTE object-level privilege on the procedure, along with one of the following:

-   SELECT object-level privilege on the view and its underlying tables
-   SELECT object-level privilege on the schema of the materialized view and its underlying tables if the schema is owned by another user



</dd>
</dl>



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_e42_1g4_jzb"/>

## Examples

```
-- Setup for the following examples ---
CREATE TABLE BAR (C1 INT, C2 INT, C3 VARCHAR(10));
CREATE MATERIALIZED VIEW MV_BAR1 AS SELECT C1, C2, C3 FROM BAR AUTO FULL REFRESH;
```

This example checks to see if materialized view MV\_BAR1 supports an automatic \(A\), incremental \(I\) refresh. Since this definition does not support this refresh and build type, the procedure returns the relevant errors in a table.

```
CALL SA_MATERIALIZED_VIEW_CAN_HAVE_REFRESH_BUILD_TYPE ('A', 'I', 'MV1', 'hdladmin');
```


<table>
<tr>
<th valign="top">

SQLStateVal

</th>
<th valign="top">

ErrorMessage

</th>
</tr>
<tr>
<td valign="top">

42WCA

</td>
<td valign="top">

The materialized view mv1 cannot be changed to incremental or immediate because it does not have a unique index on non-nullable columns.

</td>
</tr>
</table>

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-sap-hana-db-ma-7897509.md "Returns information about the specified materialized views.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-sap-hana-d-3b20ca4.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sp-iqmaterializedviewstaleness-system-procedure-for-data-lake-relational-engine-sap-hana-0342f57.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-817277b.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_materialized_view_can_have_refresh_build_type System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/7d2d2da5be7e45eaa465aa7f13cde013.html "Checks whether the materialized view supports the specified refresh and build type properties.") :arrow_upper_right:

