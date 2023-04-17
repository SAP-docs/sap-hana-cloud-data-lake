<!-- loiof7a14661f6e045398c5d4207123285e8 -->

# Terminology in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Definitions of data lake Relational Engine \(SAP HANA DB-Managed\) and SAP HANA database technical terms used in this document.

 Data Lake Relational Engine Container Group
 :   The container group is created when you provision an SAP HANA database instance with data lake Relational Engine. A data lake Relational Engine instance can only have one container group. The container group is named **SYSHDL** and cannot be changed.

  Data Lake Relational Engine Relational Container
 :   A relational container is a repository within the container group that contains data lake Relational Engine objects. Relational containers allow for the isolation of data between containers. A container group can have multiple relational containers. Each relational container name must be unique. The relational container naming convention combines the container group name with the user defined relational container name \(**SYSHDL\_*<relational\_container\_name\>***\).

  Data Lake Relational Engine *SYSRDL\#CG* Relational Container 
 :   SYSRDL\#CG is the initial relational container created in the container group in a data lake Relational Engine instance. It exists to support legacy instances.

  Relational Container Schema
 :   This schema resides in the relational container in data lake Relational Engine. It contains data lake Relational Engine objects. This schema is created when the relational container is created. You cannot create additional schemas in a relational container. The schema has the same name as the data lake Relational Engine relational container \(**SYSHDL\_*<relational\_container\_name\>***\).

  SAP HANA Database Relational Container Schema
 :   This schema resides in SAP HANA database. It contains SAP HANA database virtual tables that point to data lake Relational Engine objects in a data lake Relational Engine. This schema is created when the data lake Relational Engine relational container is created. You cannot add or remove objects from this schema. This schema owns the SAP HANA database remote source that connects the instance to data lake Relational Engine and the REMOTE\_EXECUTE procedure used to manage the relational container objects. The schema has the same naming convention as the data lake Relational Engine relational container \(**SYSHDL\_*<relational\_container\_name\>***\).

  SAP HANA Database Container Group Administrator Role
 :   This is an SAP HANA database role that is granted the privileges to create and delete relational containers. This role has no access to the data within the relational container unless privileges are explicitly granted by the administrator of a relational container. The role is named **SYSHDL\_ ROLE**.

  SAP HANA Database Container Administrator Role
 :   This is an SAP HANA database role that is granted the privileges to manage user access to a specific relational container. A user can be a member of multiple container administrator roles. Members of each container administrator role can only manage user access to that relational container unless explicitly granted by the container administrator role of that container. The role name combines the container group name, the user defined relational container name followed by \_ROLE \(**SYSHDL\_*<relational\_container\_name\>*\_ROLE**\).

  Data Lake Relational Engine System Views
 :   These are system-created views of the metadata in the data lake Relational Engine. System views are stored in the SYS schema in the container group, outside of all relational containers. Access to the SYS schema is automatically granted to all members with access to the data of any relational container.

  Data Lake Relational Engine Objects
 :   These are user-created objects within a data lake Relational Engine relational container schema, such as tables, views, and materialized views.

  Data Lake Relational Engine User-Defined Procedures and Functions
 :   These are user-created procedures and functions within a data lake Relational Engine relational container schema.

  SAP HANA Database Virtual Tables
 :   These are the tables within SAP HANA database that reference data lake Relational Engine objects. They reside in the SAP HANA database relational container schema.

  SAP HANA Database Remote Source Name
 :   The remote source is the way SAP HANA database accesses data lake Relational Engine data. There is a separate remote source for each data lake Relational Engine relational container. The naming convention of the remote source is combines the container group name and the user defined relational container name, followed by\_SOURCE \(**SYSHDL\_*<relational\_container\_name\>*\_SOURCE**\).

  SAP HANA Database REMOTE\_EXECUTE Procedure
 :   REMOTE\_EXECUTE is an SAP HANA database procedure that automatically redirects statements defined within the procedure to run in the specified data lake Relational Engine relational container. Each relational container has a dedicated REMOTE\_EXECUTE procedure with privileges specific to the specified relational container. The procedure is automatically created in the SAP HANA database relational container schema when the relational container is created.

  SAP HANA Database SYSHDL\_SOURCE Remote Source
 :   \(For internal use only.\) SYSHDL\_SOURCE is an internal remote source that facilitates cross container queries. Users have no privileges to view or use the contents of this remote source.

  Data Lake Relational Engine HDLADMIN User
 :   The HDLADMIN user is the initial data lake Relational Engine user that is automatically created when you provision a data lake Relational Engine instance integrated with SAP HANA database. It is not an SAP HANA database user. In data lake Relational Engine \(SAP HANA DB-Managed\), it has limited functionality and should only be used when indicated in a task.

 