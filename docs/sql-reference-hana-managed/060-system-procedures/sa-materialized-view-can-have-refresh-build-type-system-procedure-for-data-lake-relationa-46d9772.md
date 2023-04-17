<!-- loio46d97724fd354bb68d1c4081bd2576b0 -->

# sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Checks whether the materialized view supports the specified refresh and build type properties.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sa_materialized_view_can_have_refresh_build_type(
   <refresh_type>, <build_type>, 
   <view_name>, { <owner_name> | <schema_name> } )
```



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_vsv_nhd_bwb"/>

## Parameters

 *<refresh\_type\>* 
 :   Specifies the refresh type of the materialized view. Valid values are:

    -   I = IMMEDIATE
    -   A = AUTO
    -   M = MANUAL

  *<build\_type\>* 
 :   Specifies the build type of the materialized view. Valid values are:

    -   I = INCREMENTAL
    -   F = FULL

  *<owner\_name\>* | *<schema\_name\>*
 :   Specifies the owner of the materialized

 

<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_m1k_4hd_bwb"/>

## Results Set


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

For example, calling the procedure with the parameters A, I, MV1, HDLAMIN checks whether the materialized view MV1 owned by HDLADMIN can be altered to do an automatic \(A\), incremental \(I\) refresh.

```
sa_materialized_view_can_have_refresh_build_type('A', 'I', 'MV1', 'hdladmin')
```

If the definition does not support the refresh and build type, the procedure returns the relevant errors in a table.



<a name="loio46d97724fd354bb68d1c4081bd2576b0__section_mth_lhd_bwb"/>

## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-sap-hana-db-ma-7897509.md "Returns information about the specified materialized views.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-sap-hana-d-3b20ca4.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sp-iqmaterializedviewstaleness-system-procedure-for-data-lake-relational-engine-sap-hana-0342f57.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-817277b.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_materialized_view_can_have_refresh_build_type System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/7d2d2da5be7e45eaa465aa7f13cde013.html "Checks whether the materialized view supports the specified refresh and build type properties.") :arrow_upper_right:

