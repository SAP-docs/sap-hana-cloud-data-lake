<!-- loio05a5d3bfe1d14dd5807b9f4ac2e759f3 -->

# CREATE\_CONTAINER Procedure for SAP HANA Database

Create a new data lake Relational Engine relational container.



```
CALL SYSHDL.CREATE_CONTAINER('<relational_container_name>', '<hana_user_name>' ); 
```



<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_dj3_45x_cjb"/>

## Parameters


<dl>
<dt><b>

*<relational\_container\_name\>*

</b></dt>
<dd>

Specifies the name of the new relational container. This name must be unique.



</dd><dt><b>

*<hana\_user\_name\>*

</b></dt>
<dd>

Specifies the SAP HANA database user who is to manage the relational container.



</dd>
</dl>



<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_zhc_rnx_cjb"/>

## Description

The system procedure performs the following tasks:

-   Creates the relational container using the specified name. **\(SYSHDL\_*<relational\_container\_name\>*\)**. The owner of the relational container has the same name as the relational container.
-   Creates the container administrator role for the relational container. The SAP HANA database user specified is the default member of the container administrator role. The role name combines the relational container name with the suffix \_ROLE, **\(SYSHDL\_*<relational\_container\_name\>*\_ROLE\)**.
-   Creates the relational container user, an SAP HANA database user, which owns the SAP HANA database relational container schema and all associated procedures, servers, and sources. It is the user who communicates with the data lake Relational Engine relational container **\(SYSHDL\_*<relational\_container\_name\>*\)**.
-   Creates the default data lake Relational Engine and SAP HANA database relational container schemas. Both schemas have the same name, which is the same as the relational container name, **\(SYSHDL\_*<relational\_container\_name\>*\)**.
-   Creates the SAP HANA database remote source for the data lake Relational Engine relational container. The remote source name combines the relational container name with the suffix \_SOURCE **\(SYSHDL\_*<relational\_container\_name\>*\_SOURCE\)**.
-   Creates the remote server for the relational container. The remote server name combines the relational container name with the suffix \_SERVER **\(SYSHDL\_*<relational\_container\_name\>*\_SERVER\)**.
-   Creates the REMOTE\_EXECUTE and REMOTE\_EXECUTE\_DDL procedures, which are owned by the relational container user.
-   Grants the following permissions to the container administrator role with the ability to grant the privileges to other users and roles.
    -   EXECUTE permission on the REMOTE\_EXECUTE and REMOTE\_EXECUTE\_DDL procedures.
    -   CREATE VIRTUAL TABLE and REMOTE TABLE ADMIN permissions on the relational container remote source.
    -   SELECT, ALTER, UPDATE, INSERT, and DELETE permissions on the SAP HANA database relational container schema.




<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_xlt_rnx_cjb"/>

## Privileges

You're a member of the container group administrator role \(SYSHDL\_ROLE\).



<a name="loio05a5d3bfe1d14dd5807b9f4ac2e759f3__section_f5l_5nx_cjb"/>

## Example

The following example creates relational container CONTAINER1 and assigns USER1 as its administrator.

```
CALL SYSHDL.CREATE_CONTAINER('CONTAINER1', 'USER1');
```

-   Creates the relational container SYSHDL\_CONTAINER1. The owner of the relational container is SYSHDL\_CONTAINER1.
-   Creates the container administrator role SYSHDL\_CONTAINER1\_ROLE. The SAP HANA database user specified is the default member of the container administrator role.
-   Creates the relational container user SYSHDL\_CONTAINER1.
-   Creates the default data lake Relational Engine and SAP HANA database relational container schemas SYSHDL\_CONTAINER1\).
-   Creates the SAP HANA database remote source for the data lake Relational Engine relational container **SYSHDL\_CONTAINER1\_SOURCE**.
-   Creates the remote server for the relational container SYSHDL\_CONTAINER1\_SERVER.
-   Creates the REMOTE\_EXECUTE and REMOTE\_EXECUTE\_DDL procedures.
-   Grants the following permissions to the container administrator role with the ability to grant the privileges to other users and roles.
    -   EXECUTE permission on the REMOTE\_EXECUTE and REMOTE\_EXECUTE\_DDL procedures.
    -   CREATE VIRTUAL TABLE and REMOTE TABLE ADMIN permissions on the relational container remote source.
    -   SELECT, ALTER, UPDATE, INSERT, and DELETE permissions on the SAP HANA database relational container schema.


**Related Information**  


[Manage Relational Containers in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/0b494fedebb243fc9bd92c87bac7ddd4.html "Relational containers are managed from the SAP HANA database instance, but are stored in the data lake Relational Engine instance.") :arrow_upper_right:

[Creating a Relational Container in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/ab555a3a98204db88d1aab58b51f15ce.html "Create a relational container in the data lake Relational Engine container group.") :arrow_upper_right:

