<!-- loio0342f57672ee4657adbbfe5f124a9d48 -->

# sp\_iqmaterializedviewstaleness System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Displays staleness information about the visible version of a materialized view.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sp_iqmaterializedviewstaleness( ' <view-name>[, <owner-name> ] ' )
```



<a name="loio0342f57672ee4657adbbfe5f124a9d48__section_mys_vc2_qrb"/>

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



<a name="loio0342f57672ee4657adbbfe5f124a9d48__section_wfg_wc2_qrb"/>

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



<a name="loio0342f57672ee4657adbbfe5f124a9d48__section_ivx_djx_s3b"/>

## Privileges

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio0342f57672ee4657adbbfe5f124a9d48__section_qgk_yc2_qrb"/>

## Side Effects

None



<a name="loio0342f57672ee4657adbbfe5f124a9d48__section_mbl_pyd_xsb"/>

## Example

This example returns staleness information for materialized view M\_T10.

```
SELECT * FROM sp_iqmaterializedviewstaleness('M_T10');
```

**Related Information**  


[sa\_materialized\_view\_info System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-materialized-view-info-system-procedure-for-data-lake-relational-engine-sap-hana-db-ma-7897509.md "Returns information about the specified materialized views.")

[sa\_materialized\_view\_can\_have\_refresh\_build\_type System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-materialized-view-can-have-refresh-build-type-system-procedure-for-data-lake-relationa-46d9772.md "Checks whether the materialized view supports the specified refresh and build type properties.")

[sa\_refresh\_materialized\_views System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)](sa-refresh-materialized-views-system-procedure-for-data-lake-relational-engine-sap-hana-d-3b20ca4.md "Initializes all materialized views that are in an uninitialized state.")

[CREATE MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/create-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-816c0ee.md "Creates a materialized view.")

[REFRESH MATERIALIZED VIEW Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/refresh-materialized-view-statement-for-data-lake-relational-engine-sap-hana-db-managed-817277b.md "Initializes or refreshes the data in a materialized view by executing its query definition.")

[sp_iqmaterializedviewstaleness Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a762f3bcb4b14014821890ed5e6a25b8.html "Displays staleness information about the visible version of a materialized view.") :arrow_upper_right:

