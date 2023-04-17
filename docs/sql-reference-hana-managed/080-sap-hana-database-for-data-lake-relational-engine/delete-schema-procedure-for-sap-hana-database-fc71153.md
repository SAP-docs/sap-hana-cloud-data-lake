<!-- loiofc7115393bcc4dcba2bd9ffb53a4e49a -->

# DELETE\_SCHEMA Procedure for SAP HANA Database

Delete a data lake Relational Engine schema in a relational container.



```
CALL SYSHDL.DELETE_SCHEMA( '[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <relational_container_schema_name> (varname]' ); 
```



<a name="loiofc7115393bcc4dcba2bd9ffb53a4e49a__section_dj3_45x_cjb"/>

## Parameters

 *<relational\_container\_schema\_name\>*
 :   Specifies the name of the schema being deleted.

 

<a name="loiofc7115393bcc4dcba2bd9ffb53a4e49a__section_zhc_rnx_cjb"/>

## Description

You cannot drop a data lake Relational Engine schema that contains objects. When specifying the schema name, do not include the prefaced SYSHDL\_<relational\_container\_name\>\_ .



<a name="loiofc7115393bcc4dcba2bd9ffb53a4e49a__section_xlt_rnx_cjb"/>

## Privileges

You are a member of the container group administrator role, SYSHDL\_<relational\_container\_name\>\_ROLE.



<a name="loiofc7115393bcc4dcba2bd9ffb53a4e49a__section_f5l_5nx_cjb"/>

## Example

The following example deletes the data lake Relational Engine relational container schema MY\_SCHEMA.

```
CALL SYSHDL.DELETE_SCHEMA('MY_SCHEMA');
```

