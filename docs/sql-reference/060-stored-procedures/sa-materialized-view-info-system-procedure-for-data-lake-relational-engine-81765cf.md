<!-- loio81765cf86ce21014a6c5cb4c15fd4d22 -->

# sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine

Returns information about the specified materialized views.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_materialized_view_info( [ <view_name> [, <owner_name> ] ] )
```



<a name="loio81765cf86ce21014a6c5cb4c15fd4d22__sa_matview_info_parm1"/>

## Parameters

  *<view\_name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the name of the materialized view for which to return information. The default is NULL.

   *<owner\_name\>* 
 :   Use this optional CHAR\(128\) parameter to specify the owner of the materialized view. The default is NULL.

 

<a name="loio81765cf86ce21014a6c5cb4c15fd4d22__sa_matview_info_resultset1"/>

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

 D
 :   disabled

  E
 :   enabled

 

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

 E
 :   An error occurred during the last refresh attempt. The view is enabled, but uninitialized.

  F
 :   The underlying tables have not changed since the last refresh, and the view is considered fresh. The view is enabled and initialized.

  N
 :   The view is uninitialized. This occurs when one of the following is true:

    -   the view has not been refreshed since it was created

    -   the data has been truncated from the view

    -   the view is disabled


  S
 :   An underlying table has changed since the last refresh, and the view is considered stale. The view is enabled and initialized.

 

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

 D
 :   Use by the optimizer is disabled. The owner of the view doesn't allow the view to be used by the optimizer.

  I
 :   The view cannot be used by the optimizer for some internal reason, for example its definition doesn't meet the conditions required. However, the owner has not explicitly disallowed its use by the optimizer.

  N
 :   The view contains no data because a refresh has not been done or has failed. The view can be used by the optimizer by the owner of the view, but it is not initialized.

  O
 :   There is an incompatible option value for current connection. The view can be used by the optimizer and its definition meets all the required conditions, but the current option settings are not compatible with the options settings used to create the view.

  Y
 :   The view can be used by the optimizer. The owner of the view allows the view to be used by the optimizer and the view definition meets all the conditions needed to be used by the optimizer.

 

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

 M
 :   Manual views are refreshed manually, using the REFRESH MATERIALIZED VIEW statement or the sa\_refresh\_materialized\_views system procedure.

  A
 :   Automatic views are refreshed automatically.

 

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

 F
 :   FULL truncates the materialized view and then populates the view by fully recomputing its content.

  I
 :   INCREMENTAL attempts to refresh the materialized view using a delta computed since the last refresh. If an appropriate delta cannot be computed efficiently, then full refresh is performed.

 

</td>
</tr>
</table>



<a name="loio81765cf86ce21014a6c5cb4c15fd4d22__sa_matview_info_remarks1"/>

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



<a name="loio81765cf86ce21014a6c5cb4c15fd4d22__section_ofw_ddj_snb"/>

## Privileges

You must have EXECUTE privilege on the system procedure.



<a name="loio81765cf86ce21014a6c5cb4c15fd4d22__sa_matview_info_sideeffects1"/>

## Side Effects

All metadata for the specified materialized views, and all dependencies, are loaded into the database server cache.



The following statement returns information about all materialized views in the database:

```
SELECT *
   FROM sa_materialized_view_info();
```

The results of the sa\_materialized\_view\_info system procedure can be combined with the results of the sa\_materialized\_view\_can\_have\_refresh\_build\_type system procedure to return status information, and whether the view is eligible for being an Incremental view. Execute the following statements to create materialized views that are examined for this example:

```
CREATE MATERIALIZED VIEW view0 AS ( 
   SELECT ID, Name, Description, Size 
   FROM Products 
   WHERE Quantity > 0 );

CREATE UNIQUE INDEX u_view0 
   ON view0( ID );

ALTER MATERIALIZED VIEW view0 
   MANUAL INCREMENTAL REFRESH;

CREATE MATERIALIZED VIEW view00 AS (
   SELECT ID, Name, Description, Size 
   FROM Products 
   WHERE Quantity <= 0 );

CREATE UNIQUE INDEX u_view00 
   ON view00( ID );

CREATE MATERIALIZED VIEW view1 AS (
   SELECT ID, Name, Description, Size 
   FROM Products 
   WHERE Quantity = 0 );

ALTER MATERIALIZED VIEW view1 
   DISABLE;

CREATE MATERIALIZED VIEW view100
   AS (SELECT C.ID, C.Surname, sum(P.UnitPrice) as revenue, C.CompanyName, SO.OrderDate
         FROM Customers C, SalesOrders SO, SalesOrderItems SOI, Products P
         WHERE C.ID = SO.CustomerID
         AND SO.ID = SOI.ID
         AND P.ID = SOI.ProductID
         GROUP BY C.ID, C.Surname, C.CompanyName, SO.OrderDate);

REFRESH MATERIALIZED VIEW view100;
```

Execute the following statement to return the status and eligibility information for the views owned by you:

```
SELECT ViewName, Status, ViewLastRefreshed, AvailForOptimization, RefreshType, BuildType, CanBeIncremental
   FROM sa_materialized_view_info() AS V,
      LATERAL( SELECT LIST(ErrorMessage, ';' )
         FROM sa_materialized_view_can_have_refresh_build_type('M', 'I', V.ViewName, V.OwnerName ) ) AS I( CanBeIncremental )
   WHERE OwnerName = USER_NAME();
```


<table>
<tr>
<th valign="top">

ViewName



</th>
<th valign="top">

Status



</th>
<th valign="top">

ViewLastRefreshed



</th>
<th valign="top">

AvailForOptimization



</th>
<th valign="top">

RefreshType



</th>
<th valign="top">

BuildType



</th>
<th valign="top">

CanBeIncremental



</th>
</tr>
<tr>
<td valign="top">

view0



</td>
<td valign="top">

E



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

D



</td>
<td valign="top">

M



</td>
<td valign="top">

I



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

view00



</td>
<td valign="top">

E



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

D



</td>
<td valign="top">

M



</td>
<td valign="top">

F



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

view1



</td>
<td valign="top">

D



</td>
<td valign="top">

\(NULL\)



</td>
<td valign="top">

D



</td>
<td valign="top">

M



</td>
<td valign="top">

F



</td>
<td valign="top">

`Cannot use view 'view1' because it has been disabled.` 



</td>
</tr>
<tr>
<td valign="top">

view100



</td>
<td valign="top">

E



</td>
<td valign="top">

2022-12-19 12:53:00.000



</td>
<td valign="top">

D



</td>
<td valign="top">

M



</td>
<td valign="top">

F



</td>
<td valign="top">

 ***'The materialized view 'view100' cannot be changed to incremental or immediate because it has already been initialized. ; The materialized view cannot be changed to incremental or immediate because its SELECT list contains a SUM function over a nullable expression and it doesn't contain a COUNT function over the same expression.'*** 



</td>
</tr>
</table>

The results show that:

-   view0 was never refreshed and is an incremental view.

-   view00 was never refreshed and is a manual view.

-   view1 is disabled

-   view100 is a manual view that was last refreshed at 2022-12-19 12:53:00.000.

-   view00 can be changed to an incremental view because there are no error messages in the CanBeIncremental column.

-   view1 and view100 cannot be changed to incremental views for the reasons listed in the CanBeIncremental column.


**Related Information**  


[sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine](sa-materialized-view-can-have-refresh-build-type-system-procedure-for-data-lake-relationa-7d2d2da.md "Checks whether the materialized view supports the specified refresh and build type properties.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-8176eeb.md "Initializes all materialized views that are in an uninitialized state.")

[sp\_iqmaterializedviewstaleness Procedure for Data Lake Relational Engine](sp-iqmaterializedviewstaleness-procedure-for-data-lake-relational-engine-a762f3b.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_materialized_view_info System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/7897509ad128448889f704a5f1a80aa6.html "Returns information about the specified materialized views.") :arrow_upper_right:

