<!-- loio3beb12fb6c5f1014801ab7c27ce3cf22 -->

# SYSUSEROPTIONS System View for Data Lake Relational Engine

The SYS.SYSUSEROPTIONS view contains the option settings that are in effect for each user. If a user has no setting for an option, this view displays the public setting for the option.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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


[SYSUSERTYPE System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_1_QRC/en-US/164b9020b45548209db5cb851a82589d.html "Each row in the SYS.SYSUSERTYPE system view holds a description of a user-defined data type.") :arrow_upper_right:

