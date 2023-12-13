<!-- loio7d2d2da5be7e45eaa465aa7f13cde013 -->

# sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine

Checks whether the materialized view supports the specified refresh and build type properties.



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_materialized_view_can_have_refresh_build_type(
   '<refresh-type>', '<build-type>', 
   '<view_name>', '{ <owner-name> | <schema-name> }' );
```



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_parm1"/>

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



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_results1"/>

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



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_remarks1"/>

## Remarks

This procedure returns a table with a list of errors that prevents the specified materialized view from being altered with the specified *<refresh\_type\>* and *<build\_type\>* values.



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.

Also requires one of the following:

-   You own the underlying table of the view
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the view and its underlying tables
-   SELECT object-level privilege on the schema of the materialized view and its underlying tables if the schema is owned by another user



<a name="loio7d2d2da5be7e45eaa465aa7f13cde013__sa_matview_can_have_examples1"/>

## Examples

```
-- Setup for the following examples:
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


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-81765cf.md "Returns information about the specified materialized views.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-8176eeb.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness Procedure for Data Lake Relational Engine](sp-iqmaterializedviewstaleness-procedure-for-data-lake-relational-engine-a762f3b.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_materialized_view_can_have_refresh_build_type System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/46d97724fd354bb68d1c4081bd2576b0.html "Checks whether the materialized view supports the specified refresh and build type properties.") :arrow_upper_right:

