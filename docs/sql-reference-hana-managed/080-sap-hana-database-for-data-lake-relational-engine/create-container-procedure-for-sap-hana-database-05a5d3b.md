<!-- loio05a5d3bfe1d14dd5807b9f4ac2e759f3 -->

# CREATE\_CONTAINER Procedure for SAP HANA Database

Create a new data lake Relational Engine relational container.



```
CALL SYSHDL.CREATE_CONTAINER('[/pandoc/div/div/horizontalrule/codeblock/span/varname
     {"varname"}) <relational_container_name> (varname]', '<hana_user_name>' ); 
```



<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_dj3_45x_cjb"/>

## Parameters

 *<relational\_container\_name\>*
 :   Specifies the name of the new relational container. This name must be unique.

  *<hana\_user\_name\>*
 :   Specifies the SAP HANA database user who is to manage the relational container.

 

<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_zhc_rnx_cjb"/>

## Description

The system procedure performs the following tasks:

-   Creates the relational container using the specified name. The relational container name combines the container group name and the container group, **SYSHDL\_*<relational\_container\_name\>***.
-   Creates the container administrator role for the relational container. The role name combines the relational container name with the suffix \_ROLE \(**SYSHDL\_*<relational\_container\_name\>*\_ROLE**\). The SAP HANA database user specified becomes a member of the role as an administrator.
-   Creates the SAP HANA database and data lake Relational Engine relational container schemas. Both schemas have the same name, which is the same as the relational container name.
-   Creates the SAP HANA database remote source for the data lake Relational Engine relational container. The remote source name combines the relational container name with the suffix \_SOURCE \(**SYSHDL\_*<relational\_container\_name\>*\_SOURCE**\).
-   Grants the following permissions to the container administrator role with the ability to grant the privileges to other users and roles.
    -   EXECUTE permission on the REMOTE\_EXECUTE procedure in the SAP HANA database relational container schema.
    -   CREATE VIRTUAL TABLE and REMOTE TABLE ADMIN permissions on the relational container remote source.
    -   SELECT, ALTER, UPDATE, INSERT and DELETE permissions on the SAP HANA database relational container schema with the ability to grant the privileges to other users.




<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_xlt_rnx_cjb"/>

## Privileges

You're a member of the container group administrator role.



<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_f5l_5nx_cjb"/>

## Example

The following example creates relational container CONTAINER1 and assigns USER1 as its administrator.

```
CALL SYSHDL.CREATE_CONTAINER('CONTAINER1', 'USER1');
```

**Related Information**  


[Manage Relational Containers in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/0b494fedebb243fc9bd92c87bac7ddd4.html "A relational container is a repository within the container group that contains data lake Relational Engine objects. It allows for the isolation of data between containers and provides control over which containers a user can access.") :arrow_upper_right:

[Creating a Relational Container in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/ab555a3a98204db88d1aab58b51f15ce.html "Create a relational container in the data lake Relational Engine container group.") :arrow_upper_right:

