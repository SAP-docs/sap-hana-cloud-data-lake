<!-- loio1681f580168444a9b138cd2a8b51382b -->

# SYSVIEW System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row in the SYS.SYSVIEW system view describes a view in the database. SYS.SYSVIEW list both normal views and materialized views.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.




The tables and columns that make up this view are provided in the following SQL statement.

```
ALTER VIEW "SYS"."SYSVIEWS"( vcreator,
  viewname,viewtext ) 
  AS SELECT u.user_name,t.table_name,v.view_def
    FROM SYS.SYSTAB as t
      JOIN SYS.ISYSVIEW AS v ON(t.object_id = v.view_object_id)
      JOIN SYS.ISYSUSER AS u ON(u.user_id = t.creator);
```

You can find additional information about views in the SYS.SYSSYSTAB system view.

You can also use the dbo.sa\_materialized\_view\_info system procedure for a readable format of the information for materialized views.


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

view\_object\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the view.

</td>
</tr>
<tr>
<td valign="top">

view\_def

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

The definition \(query specification\) of the view.

</td>
</tr>
<tr>
<td valign="top">

mv\_build\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Unused.

</td>
</tr>
<tr>
<td valign="top">

mv\_refresh\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

The refresh type defined for the view. Possible values are IMMEDIATE \(1\) and MANUAL \(2\).

</td>
</tr>
<tr>
<td valign="top">

mv\_use\_in\_optimization

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Whether the materialized view can be used during query optimization \(0=can’t be used in optimization, 1=can be used in optimization\)

</td>
</tr>
<tr>
<td valign="top">

mv\_last\_refreshed\_at

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Internal use only. Indicates the local date and time that the materialized view was last refreshed.

</td>
</tr>
<tr>
<td valign="top">

mv\_known\_stale\_at

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Internal use only. The local time at which the materialized view became stale. This value corresponds to the time at which one of the underlying base tables was detected as having changed. A value of 0 indicates that the view is either fresh, or that it has become stale but the database server has not marked it as such because the view has not been used since it became stale. Use the dbo.sa\_materialized\_view\_info system procedure to determine the status of a materialized view.

</td>
</tr>
<tr>
<td valign="top">

mv\_last\_refreshed\_tsn

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The sequence number assigned to the transaction that refreshed the materialized view.

</td>
</tr>
<tr>
<td valign="top">

mv\_last\_refreshed\_at\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

Indicates the UTC date and time that the materialized view was last refreshed.

</td>
</tr>
<tr>
<td valign="top">

mv\_known\_stale\_at\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

Internal use only The UTC time at which the materialized view became stale. This value corresponds to the time at which one of the underlying base tables was detected as having changed. A value of 0 indicates that the view is either fresh, or that it has become stale but the database server has not marked it as such because the view has not been used since it became stale. Use the dbo.sa\_materialized\_view\_info system procedure to determine the status of a materialized view. This column contains 0 when mv\_last\_refreshed\_at is 0 and NULL when mv\_last\_refreshed\_at is NULL.

</td>
</tr>
</table>



<a name="loio1681f580168444a9b138cd2a8b51382b__section_t5w_n1f_xrb"/>

## Constraints on Underlying System Table

```
PRIMARY KEY (view_object_id);
```

```
FOREIGN KEY (view_object_id) references SYS.ISYSOBJECT (object_id) MATCH UNIQUE FULL; 
```



<a name="loio1681f580168444a9b138cd2a8b51382b__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSVIEWS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3beb3c476c5f10149333ff887924c019.html "Each row of the SYS.SYSVIEWS view describes one view, including its view definition.") :arrow_upper_right:

