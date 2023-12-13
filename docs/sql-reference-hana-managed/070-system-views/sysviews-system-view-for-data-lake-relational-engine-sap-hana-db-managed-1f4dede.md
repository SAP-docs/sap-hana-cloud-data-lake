<!-- loio1f4dedee333d46d1bd4c31ea6c2a440e -->

# SYSVIEWS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Each row of the SYS.SYSVIEWS view describes one view, including its view definition.



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



<a name="loio1f4dedee333d46d1bd4c31ea6c2a440e__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSVIEWS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_4_QRC/en-US/3beb3c476c5f10149333ff887924c019.html "Each row of the SYS.SYSVIEWS view describes one view, including its view definition.") :arrow_upper_right:

