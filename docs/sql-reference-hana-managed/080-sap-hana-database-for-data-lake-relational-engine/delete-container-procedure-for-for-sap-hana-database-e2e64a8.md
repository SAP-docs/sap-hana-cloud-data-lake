<!-- loioe2e64a80ae2b4ee98cebc9a7dcd027ab -->

# DELETE\_CONTAINER Procedure for for SAP HANA Database

Delete a data lake Relational Engine relational container.



```
CALL SYSHDL.DELETE_CONTAINER('[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <relational_container_name> (varname]'); 
```



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_dj3_45x_cjb"/>

## Parameters

 *<relational\_container\_name\>*
 :   Specifies the name of the relational container to delete.

 

<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_zhc_rnx_cjb"/>

## Description

The system procedure performs the following tasks:

-   Drops the empty data lake Relational Engine relational container schema.
-   Drops all objects in the SAP HANA database relational container schema and then drops the schema.
-   Drops the SAP HANA database container administrator role for the relational container.
-   Drops the SAP HANA database remote source for the relational container.
-   Drops the data lake Relational Engine relational container.

If user created objects exist in the relational container when the deletion is executed, an error message is returned warning that objects exist and the deletion fails. You cannot delete the SYSRDL\#CG relational container.



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_xlt_rnx_cjb"/>

## Privileges

You are a member of the container group administrator role.



<a name="loioe2e64a80ae2b4ee98cebc9a7dcd027ab__section_f5l_5nx_cjb"/>

## Example

The following example deletes relational container CONTAINER1.

```
CALL SYSHDL.DELETE_CONTAINER('CONTAINER1');
```

**Related Information**  


[Manage Relational Containers in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/0b494fedebb243fc9bd92c87bac7ddd4.html "A relational container is a repository within the container group that contains data lake Relational Engine objects. It allows for the isolation of data between containers and provides control over which containers a user can access.") :arrow_upper_right:

[Deleting a Relational Container in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/047e3ffb996f45d4945310e2b64efd2f.html "Delete a relational container in the container group.") :arrow_upper_right:

