<!-- loio8176eeb16ce21014bfc7bbd9e39afbab -->

# sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine

Initializes all materialized views that are in an uninitialized state.



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_refresh_materialized_views( [ <ignore_errors> ] );
```



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__sa_refresh_matviews_parm1"/>

## Parameters


<dl>
<dt><b>

*<ignore\_errors\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify whether to return errors during the recompilation. If you specify 0, an error is returned for each view for which column definition failed. If you specify 1, or any value other than 0, no errors are returned. The default is 0.



</dd>
</dl>



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__sa_refresh_matviews_results1"/>

## Results Set

None



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__sa_refresh_matviews_remarks1"/>

## Remarks

A materialized view may be in an uninitialized state because it has just been created, has just been re-enabled, or the last attempt to initialize or refresh it failed due to an error. The sa\_refresh\_materialized\_views system procedure scans the database for all such materialized views and attempts to initialize them. If the procedure encounters an error initializing a materialized view, it continues on attempting to process the remaining uninitialized views.

You can also use the REFRESH MATERIALIZED VIEW statement to initialize a materialized view.



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__sa_refresh_matviews_priv1"/>

## Privileges



### 

Requires all of the following:

-   EXECUTE object-level privilege on the procedure.
-   ALTER ANY MATERIALIZED VIEW system privilege



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__sa_refresh_matviews_sideeffects1"/>

## Side Effects

None



<a name="loio8176eeb16ce21014bfc7bbd9e39afbab__sa_refresh_matviews_examples1"/>

## Examples

This example uses the sa\_refresh\_materialized\_views system procedure to initialize all materialized views that are in an uninitialized state. Errors are ignored.

```
CALL sa_refresh_materialized_views( 1 );
```

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-81765cf.md "Returns information about the specified materialized views.")

[sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine](sa-materialized-view-can-have-refresh-build-type-system-procedure-for-data-lake-relationa-7d2d2da.md "Checks whether the materialized view supports the specified refresh and build type properties.")

[sp\_iqmaterializedviewstaleness Procedure for Data Lake Relational Engine](sp-iqmaterializedviewstaleness-procedure-for-data-lake-relational-engine-a762f3b.md "Displays staleness information about the visible version of a materialized view.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-d5c757e.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine](../080-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-faab95d.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sa_refresh_materialized_views System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/3b20ca4caa7e4ecb9000e15b95d23644.html "Initializes all materialized views that are in an uninitialized state.") :arrow_upper_right:

