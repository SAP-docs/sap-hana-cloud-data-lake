<!-- loiof7a14661f6e045398c5d4207123285e8 -->

# Terminology in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Definitions of data lake Relational Engine \(SAP HANA DB-Managed\) and SAP HANA database technical terms used in this document.


<dl>
<dt><b>

Data Lake Relational Engine Container Group

</b></dt>
<dd>

The container group contains the managed objects within the data lake Relational Engine. It is created when you provision an SAP HANA database instance with data lake Relational Engine. A data lake Relational Engine instance can only have one container group. The container group is named **SYSHDL** and cannot be renamed.



</dd><dt><b>

Data Lake Relational Engine Relational Container

</b></dt>
<dd>

A relational container is a repository within the container group that contains data lake Relational Engine objects. A container group can have multiple relational containers, with the data isolated between containers. Each relational container name must be unique and uses a naming convention that combines the container group name with the relational container name \(**SYSHDL\_*<relational\_container\_name\>***\).



</dd><dt><b>

Data Lake Relational Engine *SYSRDL\#CG* Relational Container 

</b></dt>
<dd>

The SYSRDL\#CG relational container is the default container that is created in the container group. It exists to support legacy instances and should not be used.



</dd><dt><b>

SAP HANA Database Container Group Administrator Role

</b></dt>
<dd>

This is an SAP HANA database role granted the privileges to create and delete relational containers. If granted with administrative privilege on the role, members can also manage role membership. This role has no access to the data within the relational container. The role is named **SYSHDL\_ ROLE**.



</dd><dt><b>

SAP HANA Database Container Administrator Role

</b></dt>
<dd>

This is an SAP HANA database role granted the privileges to manage objects within the a specific relational container. If granted administrative privilege on the role, members can also manage role membership. A user can be a member of multiple container administrator roles. The role name combines the container group and relational container names with the sufix \_ROLE \(**SYSHDL\_*<relational\_container\_name\>*\_ROLE**\).



</dd><dt><b>

Data Lake Relational Engine Relational Container Schemas

</b></dt>
<dd>

Relational container schemas contain data lake Relational Engine objects within the relational container. Access to the data within a schema can be controlled at the schema level, providing data isolation within a single relational container. Each relational container has one default schema, but you can add additional schemas as needed. The default schema name combines the name of the container group with the relational container name \(**SYSHDL\_*<relational\_container\_name\>***\). Additional schemas created combine the names of the container group and relational container with the name of the schema \(**SYSHDL\_*<relational\_container\_name\>*\_*<schema\_name\>***\). Schema names must be unique and cannot be renamed.



</dd><dt><b>

SAP HANA Database Relational Container Schema

</b></dt>
<dd>

The SAP HANA database relational container schema resides in the SAP HANA database database and corresponds to data lake Relational Engine relational container schema with the same name. The SAP HANA database schema has the same naming convention as the corrsponding data lake Relational Engine schemas \(**SYSHDL\_*<relational\_container\_name\>* and SYSHDL\_*<relational\_container\_name\>*\_*<schema\_name\>*** respectively\).



</dd><dt><b>

SAP HANA Database Virtual Tables

</b></dt>
<dd>

These are the tables within SAP HANA database that point to objects in a remote source. In the context of a data lake Relational Engine \(SAP HANA DB-Managed\) instance, they point to data lake Relational Engine objects that reside in a relational container schema. These virtual tables are automatically created when the data lake Relational Engine object is created and reside in the SAP HANA database relational container schema. They are automatically dropped when the corresponding data lake Relational Engine object is dropped. They cannot be manually dropped.



</dd><dt><b>

SAP HANA Database Remote Source

</b></dt>
<dd>

The remote source is the way SAP HANA database connects to data lake Relational Engine and accesses data. Each data lake Relational Engine relational container has its own dedicated remote source. The same remote source is used to access data in any schema within a single relational container. The naming convention for the remote source combines the container group and relational container names, with the suffix \_SOURCE \(**SYSHDL\_*<relational\_container\_name\>*\_SOURCE**\).



</dd><dt><b>

SAP HANA Database REMOTE\_EXECUTE Procedure

</b></dt>
<dd>

This is an SAP HANA database procedure that automatically redirects data lake Relational Engine statements defined within the procedure to run on a specified data lake Relational Engine relational container. Each relational container has a dedicated REMOTE\_EXECUTE procedure with privileges specific to a single relational container. The procedure is automatically created in the SAP HANA database relational container schema when the relational container is created. Transactions defined within the procedure run on the data lake Relational Engine worker node.



</dd><dt><b>

SAP HANA Database REMOTE\_EXECUTE\_DDL Procedure

</b></dt>
<dd>

This procedure is the same as the REMOTE\_EXECUTE procedure except that transactions defined within the procedure run on the data lake Relational Engine coordinator node, not the worker node.



</dd><dt><b>

SAP HANA Database SYSHDL\_SOURCE Remote Source

</b></dt>
<dd>

\(For internal use only.\) SYSHDL\_SOURCE is an internal remote source that facilitates cross container queries. Users have no privileges to view or use the contents of this remote source.



</dd><dt><b>

Data Lake Relational Engine HDLADMIN User

</b></dt>
<dd>

HDLADMIN is the default data lake Relational Engine user \(not an SAP HANA database user\) that is created when you provision a data lake Relational Engine instance. It allows you to directly connect to data lake Relational Engine and manage the data. By default, HDLADMIN has no privilege to data within relational containers. It must be explicitly granted by a member of the container administrator role of the relational container. For more information, see [Relational Containers and HDLADMIN in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2024_3_QRC/en-US/8511271f325c49aa87713e815f4708c9.html "Relational containers are isolated from each other, and the HDLADMIN user, by design.") :arrow_upper_right:.



</dd>
</dl>

