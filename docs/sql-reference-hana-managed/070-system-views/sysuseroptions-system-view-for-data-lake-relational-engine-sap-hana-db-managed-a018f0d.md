<!-- loioa018f0df6763447ab609c4ab1da372e4 -->

# SYSUSEROPTIONS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The SYS.SYSUSEROPTIONS view contains the option settings that are in effect for each user. If a user has no setting for an option, this view displays the public setting for the option.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:

-   Connected to SAP HANA database as a SAP HANA database user, and using SAP HANA database REMOTE\_EXECUTE\_QUERY.




The tables and columns that make up this view are provided in the following SQL statement. To learn more about a particular table or column, use the links provided beneath the view definition.

```
ALTER VIEW "SYS"."SYSUSEROPTIONS"( user_name,
  "option",setting ) 
  AS SELECT u.user_name,
    o."option",
    ISNULL((select s.setting
      FROM SYS.ISYSOPTION AS s
      WHERE s.user_id = u.user_id
      AND s."option" = o."option"),
    o.setting)
    FROM SYS.SYSOPTIONS AS o,SYS.ISYSUSER AS u
    WHERE o.user_name = 'PUBLIC';
```



<a name="loioa018f0df6763447ab609c4ab1da372e4__section_gj1_wy1_4yb"/>

## Privileges

To use SAP HANA database REMOTE\_EXECUTE\_QUERY requires the REMOTE EXECUTE privilege on the remote source <hana\_relational\_container\_schema\>\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](https://help.sap.com/docs/SAP_HANA_DATA_LAKE/a898e08b84f21015969fa437e89860c8/ada51c0074354a5f99b60c14cffb653c.html).

**Related Information**  


[SYSUSEROPTIONS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/3beb12fb6c5f1014801ab7c27ce3cf22.html "The SYS.SYSUSEROPTIONS view contains the option settings that are in effect for each user. If a user has no setting for an option, this view displays the public setting for the option.") :arrow_upper_right:

