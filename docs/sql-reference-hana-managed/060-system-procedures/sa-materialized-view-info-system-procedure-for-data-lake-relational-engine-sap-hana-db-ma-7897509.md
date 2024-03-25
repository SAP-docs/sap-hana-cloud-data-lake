<!-- loio7897509ad128448889f704a5f1a80aa6 -->

# sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns information about the specified materialized views.



<a name="loio7897509ad128448889f704a5f1a80aa6__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_materialized_view_info( [ '<view-name>', '<schema-name>' ] )
```



<a name="loio7897509ad128448889f704a5f1a80aa6__section_i2f_5zd_srb"/>

## Parameters


<dl>
<dt><b>

*<view-name\>* 

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the name of the materialized view for which to return information. The default is NULL.



</dd><dt><b>

*<schema-name\>* 

</b></dt>
<dd>

Specify the user-created schema name for the *<table-name\>*. The referenced table must reside in a user-created schema in a relational container. It cannot reside in the default schema \(SYSHDL\_*<relational\_container\_name\>*\).



</dd>
</dl>



<a name="loio7897509ad128448889f704a5f1a80aa6__section_jlv_5zd_srb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

OwnerName

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The owner of the view.

</td>
</tr>
<tr>
<td valign="top">

ViewName

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the view.

</td>
</tr>
<tr>
<td valign="top">

Status

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Status information about the view. Possible values are:


<dl>
<dt><b>

D

</b></dt>
<dd>

disabled



</dd><dt><b>

E

</b></dt>
<dd>

enabled



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

DataStatus

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Status information about data in the view. Possible values are:


<dl>
<dt><b>

E

</b></dt>
<dd>

An error occurred during the last refresh attempt. The view is enabled, but uninitialized.



</dd><dt><b>

F

</b></dt>
<dd>

The underlying tables have not changed since the last refresh, and the view is considered fresh. The view is enabled and initialized.



</dd><dt><b>

N

</b></dt>
<dd>

The view is uninitialized. This occurs when one of the following is true:

-   the view has not been refreshed since it was created

-   the data has been truncated from the view

-   the view is disabled




</dd><dt><b>

S

</b></dt>
<dd>

An underlying table has changed since the last refresh, and the view is considered stale. The view is enabled and initialized.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

ViewLastRefreshed

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The database server local date and time when the view was last refreshed. If the value of ViewLastRefreshed is NULL, the view is uninitialized. This value is affected by simulated time zone.

</td>
</tr>
<tr>
<td valign="top">

DataLastModified

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

For a stale view, the last database server local date and time that underlying data was modified. This value is affected by simulated time zone.

The value is NULL for views that are not initialized, or for views that are not considered stale.

</td>
</tr>
<tr>
<td valign="top">

AvailForOptimization

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Information about the availability of the view for use by the optimizer. Possible values are:


<dl>
<dt><b>

D

</b></dt>
<dd>

Use by the optimizer is disabled. The owner of the view doesn't allow the view to be used by the optimizer.



</dd><dt><b>

I

</b></dt>
<dd>

The view cannot be used by the optimizer for some internal reason, for example its definition doesn't meet the conditions required. However, the owner has not explicitly disallowed its use by the optimizer.



</dd><dt><b>

N

</b></dt>
<dd>

The view contains no data because a refresh has not been done or has failed. The view can be used by the optimizer by the owner of the view, but it is not initialized.



</dd><dt><b>

O

</b></dt>
<dd>

There is an incompatible option value for current connection. The view can be used by the optimizer and its definition meets all the required conditions, but the current option settings are not compatible with the options settings used to create the view.



</dd><dt><b>

Y

</b></dt>
<dd>

The view can be used by the optimizer. The owner of the view allows the view to be used by the optimizer and the view definition meets all the conditions needed to be used by the optimizer.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

RefreshType

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

The refresh type for the view. Possible values are:


<dl>
<dt><b>

M

</b></dt>
<dd>

Manual views are refreshed manually, using the REFRESH MATERIALIZED VIEW statement or the sa\_refresh\_materialized\_views system procedure.



</dd><dt><b>

A

</b></dt>
<dd>

Automatic views are refreshed automatically.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

BuildType

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

The refresh build method for the view. Possible values are:


<dl>
<dt><b>

F

</b></dt>
<dd>

FULL truncates the materialized view and then populates the view by fully recomputing its content.



</dd><dt><b>

I

</b></dt>
<dd>

INCREMENTAL attempts to refresh the materialized view using a delta computed since the last refresh. If an appropriate delta cannot be computed efficiently, then full refresh is performed.



</dd>
</dl>



</td>
</tr>
</table>



<a name="loio7897509ad128448889f704a5f1a80aa6__section_snq_vzd_srb"/>

## Remarks

If neither *<view\_name\>* nor *<owner\_name\>* are specified or both are NULL, information about all materialized views in the database is returned.

If *<owner\_name\>* is not specified or is NULL, information about all materialized views named *<view\_name\>* is returned.

This procedure can be useful for determining the list of materialized views that will never be considered by the optimizer because of a problem with the view definition. The AvailForOptimization value is **I** for these materialized views.

The following table shows how the AvailForOptimization property is determined. Starting from the left column, you read across the row to see the conditions that must be in place to result in the value found in the AvailForOptimization column.


<table>
<tr>
<th valign="top">

User allows view to be used in optimization?

</th>
<th valign="top">

The view definition satisfies all the conditions required for use?

</th>
<th valign="top">

The connection options match those required for use of the view?

</th>
<th valign="top">

The view is initialized?

</th>
<th valign="top">

AvailForOptimization value

</th>
</tr>
<tr>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Y

</td>
</tr>
<tr>
<td valign="top">

No

</td>
<td valign="top">

N/A

</td>
<td valign="top">

N/A

</td>
<td valign="top">

N/A

</td>
<td valign="top">

D

</td>
</tr>
<tr>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

N/A

</td>
<td valign="top">

Yes

</td>
<td valign="top">

I

</td>
</tr>
<tr>
<td valign="top">

Yes

</td>
<td valign="top">

N/A

</td>
<td valign="top">

N/A

</td>
<td valign="top">

No

</td>
<td valign="top">

N

</td>
</tr>
<tr>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

No

</td>
<td valign="top">

Yes

</td>
<td valign="top">

O

</td>
</tr>
</table>

An initialized materialized view can be empty. This occurs when there is no data in the underlying tables that meets the materialized view definition. An empty view is not considered the same as an uninitialized materialized view, which also has no data in it. The value of the ViewLastRefreshed property allows you to distinguish between whether the view is uninitialized \(NULL\), or empty because of data in the underlying tables \(non-NULL\).

The results of the sa\_materialized\_view\_info system procedure can be combined with the results of the sa\_materialized\_view\_can\_have\_refresh\_build\_type system procedure to return status information, and whether the view is eligible for being an Incremental view.



<a name="loio7897509ad128448889f704a5f1a80aa6__section_adk_1z1_1yb"/>

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

Requires EXECUTE object-level privilege on the procedure along with one of the following:

-   SELECT object-level privilege on the view and its underlying tables
-   SELECT object-level privilege on the schema of the materialized view and its underlying tables



</dd>
</dl>



<a name="loio7897509ad128448889f704a5f1a80aa6__section_ngp_wzd_srb"/>

## Side Effects

All metadata for the specified materialized views, and all dependencies, are loaded into the database server cache.



## Examples

This example uses the sa\_materialized\_view\_info system procedure to return information about all materialized views in the database:

```
CALL sa_materialized_view_info();
```


<table>
<tr>
<th valign="top">

OwnerName

</th>
<th valign="top">

ViewName

</th>
<th valign="top">

Status

</th>
<th valign="top">

DataStatus

</th>
<th valign="top">

ViewLastRefreshed

</th>
<th valign="top">

DataLastModified

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

V\_BAR1

</td>
<td valign="top">

E

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

m\_t1

</td>
<td valign="top">

E

</td>
<td valign="top">

F

</td>
<td valign="top">

03:00.0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

mv1

</td>
<td valign="top">

E

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="3">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

AvailForOptimization

</th>
<th valign="top">

RefreshType

</th>
<th valign="top">

BuildType

</th>
</tr>
<tr>
<td valign="top">

D

</td>
<td valign="top">

A

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

D

</td>
<td valign="top">

A

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

D

</td>
<td valign="top">

A

</td>
<td valign="top">

F

</td>
</tr>
</table>

This example returns information about materialized view V\_BAR1, owned by USER1:

```
CALL sa_materialized_view_info('V_BAR1', 'USER1);
```


<table>
<tr>
<th valign="top">

OwnerName

</th>
<th valign="top">

ViewName

</th>
<th valign="top">

Status

</th>
<th valign="top">

DataStatus

</th>
<th valign="top">

ViewLastRefreshed

</th>
<th valign="top">

DataLastModified

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

V\_BAR1

</td>
<td valign="top">

E

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="3">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

AvailForOptimization

</th>
<th valign="top">

RefreshType

</th>
<th valign="top">

BuildType

</th>
</tr>
<tr>
<td valign="top">

D

</td>
<td valign="top">

A

</td>
<td valign="top">

F

</td>
</tr>
</table>

**Related Information**  


[sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-materialized-view-can-have-refresh-build-type-system-procedure-for-data-lake-relationa-46d9772.md "Checks whether the materialized view supports the specified refresh and build type properties.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-sap-hana-d-3b20ca4.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sp-iqmaterializedviewstaleness-system-procedure-for-data-lake-relational-engine-sap-hana-0342f57.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-817277b.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_materialized_view_info System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_1_QRC/en-US/81765cf86ce21014a6c5cb4c15fd4d22.html "Returns information about the specified materialized views.") :arrow_upper_right:

