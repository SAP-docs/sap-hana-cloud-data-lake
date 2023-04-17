<!-- loio3ee2d49bdc034355aed528d92a426c3b -->

# RECONCILE Procedure for SAP HANA Database

Manually synchronize the objects in a data lake Relational Engine relational container with the corresponding SAP HANA database relational container schema.



```
CALL SYSHDL_[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <relational_container_schema_name> (varname].RECONCILE()
```



<a name="loio3ee2d49bdc034355aed528d92a426c3b__section_xlt_rnx_cjb"/>

## Privileges

You are a member of the container group administrator role, SYSHDL\_*<relational\_container\_schema\_name\>*\_ROLE.



<a name="loio3ee2d49bdc034355aed528d92a426c3b__section_f5l_5nx_cjb"/>

## Example

The following example synchronizes all objects in data lake Relational Engine relational container CONTAINER1 with objects in the corresponding SAP HANA database relational container schema. If objects are found in the data lake Relational Engine relational container but not in SAP HANA database relational container, then data lake Relational Engine automatically attempts to create the missing SAP HANA database virtual table. If the virtual table cannot be created, an error message appears.

```
CALL SYSHDL.CONTAINER1.RECONCILE();
```

