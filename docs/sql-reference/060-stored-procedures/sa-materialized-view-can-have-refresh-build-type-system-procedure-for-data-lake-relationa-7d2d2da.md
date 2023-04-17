<!-- loio7d2d2da5be7e45eaa465aa7f13cde013 -->

# sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine

Checks whether the materialized view supports the specified refresh and build type properties.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_materialized_view_can_have_refresh_build_type(
   <refresh_type>, <build_type>, 
   <view_name>, { <owner_name> | <schema_name> } )
```



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_parm1"/>

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

 

<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_results1"/>

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



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_remarks1"/>

## Remarks

This procedure returns a table with a list of errors that prevents the specified materialized view from being altered with the specified *<refresh\_type\>* and *<build\_type\>* values.

For example, calling the procedure with the parameters A, I, MV1, HDLAMIN checks whether the materialized view MV1 owned by HDLADMIN can be altered to do an automatic \(A\), incremental \(I\) refresh.

```
sa_materialized_view_can_have_refresh_build_type('A', 'I', 'MV1', 'hdladmin')
```

If the definition does not support the refresh and build type, the procedure returns the relevant errors in a table.



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__section_ofw_ddj_snb"/>

## Privileges

You must have EXECUTE privilege on the system procedure.

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-81765cf.md "Returns information about the specified materialized views.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-8176eeb.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness Procedure for Data Lake Relational Engine](sp-iqmaterializedviewstaleness-procedure-for-data-lake-relational-engine-a762f3b.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_materialized_view_can_have_refresh_build_type System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/46d97724fd354bb68d1c4081bd2576b0.html "Checks whether the materialized view supports the specified refresh and build type properties.") :arrow_upper_right:

