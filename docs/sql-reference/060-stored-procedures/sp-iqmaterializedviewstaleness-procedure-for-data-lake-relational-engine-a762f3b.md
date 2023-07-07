<!-- loioa762f3bcb4b14014821890ed5e6a25b8 -->

# sp\_iqmaterializedviewstaleness Procedure for Data Lake Relational Engine

Displays staleness information about the visible version of a materialized view.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmaterializedviewstaleness( ' <view-name>[, <owner-name> ] ' )
```



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_parm1"/>

## Parameter


<dl>
<dt><b>

*<view-name\>*

</b></dt>
<dd>

The name of the materialized view.



</dd><dt><b>

*<owner-name\>*

</b></dt>
<dd>

The owner of the materialized view.



</dd>
</dl>



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_returns1"/>

## Returns

sp\_iqmaterializedviewstaleness displays the following information:


<table>
<tr>
<th valign="top">

Column



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

view\_owner



</td>
<td valign="top">

varchar\(257\)



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

varchar\(257\)



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

char\(1\),



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

INTEGER



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

TIMESTAMP



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

TIMESTAMP



</td>
<td valign="top">

The start time of the active transaction.



</td>
</tr>
</table>



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_sideeffects1"/>

## Side Effects

None



<a name="loioa762f3bcb4b14014821890ed5e6a25b8__sp_iqmaterializedviewstaleness_example1"/>

## Example

This example returns staleness information for materialized view M\_T10.

```
SELECT * FROM sp_iqmaterializedviewstaleness('M_T10');
```

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-81765cf.md "Returns information about the specified materialized views.")

[sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine](sa-materialized-view-can-have-refresh-build-type-system-procedure-for-data-lake-relationa-7d2d2da.md "Checks whether the materialized view supports the specified refresh and build type properties.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-8176eeb.md "Initializes all materialized views that are in an uninitialized state.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sp_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/0342f57672ee4657adbbfe5f124a9d48.html "Displays staleness information about the visible version of a materialized view.") :arrow_upper_right:

