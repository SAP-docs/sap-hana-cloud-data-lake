<!-- loioa018f0df6763447ab609c4ab1da372e4 -->

# SYSUSEROPTIONS System View for Data Lake Relational Engine \(SAP HANA DB-Managed\)

The SYS.SYSUSEROPTIONS view contains the option settings that are in effect for each user. If a user has no setting for an option, this view displays the public setting for the option.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system view can be used when connected as follows:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Viewing System Views](remote-execute-usage-examples-for-viewing-system-views-8b235c7.md).
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE\_QUERY procedure.
> 
>     -   See [REMOTE\_EXECUTE\_QUERY Usage Examples for Viewing System Views](remote-execute-query-usage-examples-for-viewing-system-views-ada51c0.md).



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
    WHERE o.user_name = 'PUBLIC'
```

**Related Information**  


[SYSUSEROPTIONS System View for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/3beb12fb6c5f1014801ab7c27ce3cf22.html "The SYS.SYSUSEROPTIONS view contains the option settings that are in effect for each user. If a user has no setting for an option, this view displays the public setting for the option.") :arrow_upper_right:

