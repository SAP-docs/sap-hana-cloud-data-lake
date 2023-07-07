<!-- loiof7a14661f6e045398c5d4207123285e8 -->

# Terminology in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Definitions of data lake Relational Engine \(SAP HANA DB-Managed\) and SAP HANA database technical terms used in this document.


<dl>
<dt><b>

Data Lake Relational Engine Container Group

</b></dt>
<dd>

The container group is created when you provision an SAP HANA database instance with data lake Relational Engine. A data lake Relational Engine instance can only have one container group. The container group is named **SYSHDL** and cannot be renamed.



</dd><dt><b>

Data Lake Relational Engine Relational Container

</b></dt>
<dd>

A relational container is a repository within the container group that contains data lake Relational Engine objects. A container group can have multiple relational containers, with the data isolated between containers. Each relational container name must be unique and uses a naming convention that combines the container group name with the user defined relational container name \(**SYSHDL\_*<relational\_container\_name\>***\).



</dd><dt><b>

Data Lake Relational Engine *SYSRDL\#CG* Relational Container 

</b></dt>
<dd>

The SYSRDL\#CG relational container is the default container that is created in the container group. It exists to support legacy instances and should not be used.



</dd><dt><b>

SAP HANA Database Container Group Administrator Role

</b></dt>
<dd>

This is an SAP HANA database role that is granted the privileges to create and delete relational containers. This role has no access to the data within the relational container unless privileges are explicitly granted by the administrator of a relational container. The role is named **SYSHDL\_ ROLE**.



</dd><dt><b>

SAP HANA Database Container Administrator Role

</b></dt>
<dd>

This is an SAP HANA database role that is granted the privileges to manage user access to a specific relational container. A user can be a member of multiple container administrator roles. Members of each container administrator role can only manage user access to that relational container unless explicitly granted privilege by the container administrator role of another container. The role name combines the container group name and the user defined relational container name with \_ROLE \(**SYSHDL\_*<relational\_container\_name\>*\_ROLE**\).



</dd><dt><b>

Data Lake Relational Engine Relational Container Schemas

</b></dt>
<dd>

Relational container schemas exist within the relational container. They allow you to further isolate data within a single relational container. Each relational container has one default schema, but you can add additional schemas as needed. Schemas contain data lake Relational Engine objects. The default schema name is prefaced with the name of the container group \(SYSHDL\) and the name of the relational container \(**SYSHDL\_*<relational\_container\_name\>***\). Additional schemas created preface the specified schema name with the container group and relational container names \(**SYSHDL\_*<relational\_container\_name\>*\_*<schema\_name\>***\). Once create, schema names cannot be changed.



</dd><dt><b>

SAP HANA Database Relational Container Schema

</b></dt>
<dd>

The SAP HANA database relational container schema resides in the SAP HANA database database and contains the automatically created SAP HANA database virtual tables that point to the corresponding data lake Relational Engine objects in the data lake Relational Engine relational container schema. This schema is created when the first data lake Relational Engine object is created. You cannot add or remove objects from this schema. This schema owns the SAP HANA database remote source that connects the instance to the corresponding data lake Relational Engine relational container and the REMOTE\_EXECUTE procedure used to manage the objects in the relational container. The schema has the same naming convention as the data lake Relational Engine relational container \(**SYSHDL\_*<relational\_container\_name\>* and SYSHDL\_*<relational\_container\_name\>*\_*<schema\_name\>***\).



</dd><dt><b>

Data Lake Relational Engine System Views

</b></dt>
<dd>

These are system-created views of the metadata in the data lake Relational Engine. System views are stored in the SYS schema in the container group, outside of all relational containers. Access to the SYS schema is automatically granted to all members with access to the data of any relational container.



</dd><dt><b>

Data Lake Relational Engine Objects

</b></dt>
<dd>

These are user-created objects within a data lake Relational Engine relational container schema.



</dd><dt><b>

SAP HANA Database Virtual Tables

</b></dt>
<dd>

These are the tables within SAP HANA database that point to objects in a remote source. In the context of a data lake Relational Engine \(SAP HANA DB-Managed\) instance, they point to data lake Relational Engine objects that reside in a relational container schema. These virtual tables are automatically created when the data lake Relational Engine object is created and reside in the SAP HANA database relational container schema. They are automatically dropped when the corresponding data lake Relational Engine object is dropped. They cannot be manually dropped.



</dd><dt><b>

SAP HANA Database Remote Source

</b></dt>
<dd>

The remote source is the way SAP HANA database connects to data lake Relational Engine and accesses data. Each data lake Relational Engine relational container has its own dedicated remote source. The remote source has access to data in all schemas within the same data lake Relational Engine. The naming convention for the remote source combines the container group name \(SYSHDL\) and the relational container name, with \_SOURCE \(**SYSHDL\_*<relational\_container\_name\>*\_SOURCE**\).



</dd><dt><b>

SAP HANA Database REMOTE\_EXECUTE Procedure

</b></dt>
<dd>

This is an SAP HANA database procedure that automatically redirects statements defined within the procedure to run in the specified data lake Relational Engine relational container. Each relational container has a dedicated REMOTE\_EXECUTE procedure with privileges specific to the specified relational container. The procedure is automatically created in the SAP HANA database relational container schema when the relational container is created.



</dd><dt><b>

SAP HANA Database SYSHDL\_SOURCE Remote Source

</b></dt>
<dd>

\(For internal use only.\) SYSHDL\_SOURCE is an internal remote source that facilitates cross container queries. Users have no privileges to view or use the contents of this remote source.



</dd><dt><b>

Data Lake Relational Engine HDLADMIN User

</b></dt>
<dd>

HDLADMIN is the default data lake Relational Engine user \(not an SAP HANA database user\) that is created when you provision a data lake Relational Engine instance. It allows you to directly connect to data lake Relational Engine and manage the data. By default, HDLADMIN has no privilege to data within relational containers. It must be explicitly granted by the container administrator role of the relational containers. For more information, see [HDLADMIN and Relational Containers in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/8511271f325c49aa87713e815f4708c9.html "Relational containers are isolated from each other and HDLADMIN by design.") :arrow_upper_right:.



</dd>
</dl>

