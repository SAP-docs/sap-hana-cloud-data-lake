<!-- loioa762f3bcb4b14014821890ed5e6a25b8 -->

# sp\_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine

Displays staleness information about the visible version of a materialized view.



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmaterializedviewstaleness( '<view-name>'[, '{ <owner-name> | <schema-name> }' ] )
```



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_parm1"/>

## Parameters


<dl>
<dt><b>

*<view-name\>*

</b></dt>
<dd>

The name of the materialized view.



</dd><dt><b>

*<owner-name\>* | *<schema-name\>*

</b></dt>
<dd>

Use this optional CHAR\(128\) parameter to specify the owner or schema name for the *<view-name\>*. The default is NULL.



</dd>
</dl>



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_returns1"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

view\_owner

</td>
<td valign="top">

The owner of the materialized view.

</td>
</tr>
<tr>
<td valign="top">

view\_name

</td>
<td valign="top">

The name of the materialized view.

</td>
</tr>
<tr>
<td valign="top">

stale

</td>
<td valign="top">

The staleness of the materialized view relative to the active transaction:

-   F = the materialized view is fresh relative to the active transaction
-   S = the materialized view is stale relative to the active transaction



</td>
</tr>
<tr>
<td valign="top">

stale\_time

</td>
<td valign="top">

The amount of time, in minutes, that the visible version of the materialized view has been stale relative to the start time of the active transaction or NULL if the materialized view is fresh.

</td>
</tr>
<tr>
<td valign="top">

known\_stale\_time

</td>
<td valign="top">

The known stale time for the visible version of the materialized view, or NULL if it is fresh. The known stale time may be non-NULL even if the materialized view is fresh. This occurs if a transaction not visible to the querying transaction makes a change to a base table and commits.

</td>
</tr>
<tr>
<td valign="top">

txn\_begin\_time

</td>
<td valign="top">

The start time of the active transaction.

</td>
</tr>
</table>



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.

Also requires one of the following:

-   You own the materialized view
-   SELECT object-level privilege on the materialized view.



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_sideeffects1"/>

## Side Effects

None.



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_example1"/>

## Examples

This example returns staleness information for materialized view MV\_T10 owned by USER1.

```
CALL sp_iqmaterializedviewstaleness('MV_T10','USER1');
```


<table>
<tr>
<th valign="top">

view\_owner

</th>
<th valign="top">

view\_name

</th>
<th valign="top">

stale

</th>
<th valign="top">

stale\_time

</th>
<th valign="top">

known\_stale\_time

</th>
<th valign="top">

txn\_begin\_time

</th>
</tr>
<tr>
<td valign="top">

USER1

</td>
<td valign="top">

MV\_T10

</td>
<td valign="top">

F

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

24:44.0

</td>
</tr>
</table>

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-81765cf.md "Returns information about the specified materialized views.")

[sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine](sa-materialized-view-can-have-refresh-build-type-system-procedure-for-data-lake-relationa-7d2d2da.md "Checks whether the materialized view supports the specified refresh and build type properties.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-8176eeb.md "Initializes all materialized views that are in an uninitialized state.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sp_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/0342f57672ee4657adbbfe5f124a9d48.html "Displays staleness information about the visible version of a materialized view.") :arrow_upper_right:

