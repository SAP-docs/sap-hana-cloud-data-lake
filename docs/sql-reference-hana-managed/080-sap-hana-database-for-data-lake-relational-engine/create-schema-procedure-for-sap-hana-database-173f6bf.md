<!-- loio173f6bf8e1614f6eaae5523084be64db -->

# CREATE\_SCHEMA Procedure for SAP HANA Database

Create a new data lake Relational Engine schema in a relational container.



```
CALL SYSHDL.CREATE_SCHEMA( '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <relational_container_schema_name> (varname]' ); 
```



<a name="loio173f6bf8e1614f6eaae5523084be64db__section_dj3_45x_cjb"/>

## Parameters

 *<relational\_container\_schema\_name\>*
 :   Specifies the name of the new schema in the relational container. This name must be unique.

 

<a name="loio173f6bf8e1614f6eaae5523084be64db__section_zhc_rnx_cjb"/>

## Description

The schema name combines the name of the relational container and the name of the schema and is prefaced with SYSHDL \(SYSHDL\_*<relational\_container\_name\>*\_*<relational\_container\_schema\_name\>*\). The corresponding SAP HANA database relational container schema, with the same name, is not created until the first object is created in the data lake Relational Engine relational container schema.



<a name="loio173f6bf8e1614f6eaae5523084be64db__section_xlt_rnx_cjb"/>

## Privileges

You are a member of the container group administrator role, SYSHDL\_<relational\_container\_name\>\_ROLE.



<a name="loio173f6bf8e1614f6eaae5523084be64db__section_f5l_5nx_cjb"/>

## Example

The following example creates relational container CONTAINER1 and assigns USER1 as its administrator.

```
CALL SYSHDL.CREATE_SCHEMA('MY_SCHEMA');
```

