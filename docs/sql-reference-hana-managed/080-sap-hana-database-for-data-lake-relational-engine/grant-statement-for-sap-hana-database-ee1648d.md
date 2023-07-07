<!-- loioee1648d43b994f44b457a1dba6072442 -->

# GRANT Statement for SAP HANA Database

Grant privileges to users and roles to manage and query data lake Relational Engine data.



<a name="loioee1648d43b994f44b457a1dba6072442__sql_grant_1sql_grant_syntax"/>

## Syntax

```
GRANT <system_privilege> [,...] TO <grantee> [ WITH ADMIN OPTION ]
 | GRANT <source_privilege>[{, <source_privilege>}...] ON REMOTE SOURCE SYSHDL_<relational_container_name>_SOURCE TO <grantee> [ WITH GRANT OPTION ]
 | GRANT <schema_privilege> [,...] ON SCHEMA <hana_relational_container_schema_name> TO <grantee> [ WITH GRANT OPTION ]
 | GRANT <object_privilege> [,...] ON <hana_relational_container_schema_name>.<hana_object_name> TO <grantee> [ WITH GRANT OPTION ]
 | GRANT <role_name> [,...] TO <grantee> [ WITH ADMIN OPTION ]
```



<a name="loioee1648d43b994f44b457a1dba6072442__sql_grant_1sql_grant_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<grantee\>*

</b></dt>
<dd>

Specifies the user or role that the privilege is being granted to. A role is a named collection of privileges and can be granted to either a user or another role.

```
<grantee> :: = { <user_name> | <role_name> }
```

```
<user_name> ::= <unicode_name>
```

```
<role_name> ::= [ <hana_relational_container_schema_name>].<identifier>
```

If a privilege or role is granted to a role, then all users granted that role have the specified privilege or role.

If you want to allow several database users to perform the same actions, then create a role, grant the required privileges to this role, and finally grant the role to the different database users.

When granting roles to roles, a tree of roles can be built. When granting a role \(R\) to a role or user \(G\), user G has all the privileges directly granted to role R and all privileges granted to roles that have been granted to role R.

*<user\_name\>* specifies the grantee's user name.

*<role\_name\>* specifies the grantee's role name with optional schema name.

A reference to a schema-local role \(that is, a role for which a schema\_name was specified at creation time\), must always be preceded by its *<hana\_relational\_container\_schema\_name\>* wherever it is referenced \(for example, <code>GRANT <b><i class="varname">&lt;hana_relational_container_schema_name&gt;</i></b>.<i class="varname">&lt;role_name&gt;</i> TO...)</code>.



</dd><dt><b>

*<system\_privilege\>*

</b></dt>
<dd>

Grants the specified system privilege.

```
<system_privilege> ::= 
```


<table>
<tr>
<td valign="top">

ADAPTER ADMIN

| AGENT ADMIN

| ATTACH DEBUGGER

| AUDIT ADMIN

| AUDIT OPERATOR

| AUDIT READ

| CATALOG READ

| CERTIFICATE ADMIN

| CLIENT PARAMETER ADMIN

| CREATE JWT PROVIDER

| CREATE REMOTE SOURCE

| CREATE SAML PROVIDER

| CREATE SCENARIO

| CREATE SCHEMA

| CREATE USERGROUP

| CREATE X509 PROVIDER

| CREDENTIAL ADMIN

| DATABASE ADMIN

| EXPORT

| IMPORT

| INIFILE ADMIN



</td>
<td valign="top">

| LDAP ADMIN

| LOG ADMIN

| MONITOR ADMIN

| OPTIMIZER ADMIN

| RESOURCE ADMIN

| ROLE ADMIN

| SAVEPOINT ADMIN

| SCENARIO ADMIN

| SERVICE ADMIN

| SESSION ADMIN

| SSL ADMIN

| TABLE ADMIN

| TRACE ADMIN

| TRUST ADMIN

| WORKLOAD ADMIN

| WORKLOAD ANALYZE ADMIN

| WORKLOAD CAPTURE ADMIN

| WORKLOAD REPLAY ADMIN

*<identifier\>*.*<identifier\>*



</td>
</tr>
</table>

System privileges restrict administrative tasks. The following table describes the supported system privileges in an SAP HANA database.


<table>
<tr>
<th valign="top">

System Privilege



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

ADAPTER ADMIN



</td>
<td valign="top">

Controls the execution of the following adapter-related statements: CREATE ADAPTER, DROP ADAPTER, and ALTER ADAPTER. It also allows access to the ADAPTERS and ADAPTER\_LOCATIONS system views.



</td>
</tr>
<tr>
<td valign="top">

AGENT ADMIN



</td>
<td valign="top">

Controls the execution of the following agent-related statements: CREATE AGENT, DROP AGENT, and ALTER AGENT. It also allows access to the AGENTS and ADAPTER\_LOCATIONS system views.



</td>
</tr>
<tr>
<td valign="top">

ATTACH DEBUGGER



</td>
<td valign="top">

Authorizes debugging across different user sessions. For example, userA can grant ATTACH DEBUGGER to userB to allow userB to debug a procedure in userA’s session \(userB still needs DEBUG privilege on the procedure, however\).



</td>
</tr>
<tr>
<td valign="top">

AUDIT ADMIN



</td>
<td valign="top">

Controls the execution of the following auditing-related statements: CREATE AUDIT POLICY, DROP AUDIT POLICY, and ALTER AUDIT POLICY, as well as changes to the auditing configuration. It also allows access to the AUDIT\_LOG and ALL\_AUDIT\_LOG system views.



</td>
</tr>
<tr>
<td valign="top">

AUDIT OPERATOR



</td>
<td valign="top">

Authorizes the execution of the following statement: ALTER SYSTEM CLEAR AUDIT LOG. It also allows access to the AUDIT\_LOG system view.



</td>
</tr>
<tr>
<td valign="top">

AUDIT READ



</td>
<td valign="top">

Authorizes read-only access to the rows of the AUDIT\_LOG, and ALL\_AUDIT\_LOG system views.



</td>
</tr>
<tr>
<td valign="top">

CATALOG READ



</td>
<td valign="top">

Authorizes unfiltered access to the data in the system views that a user has already been granted the SELECT privilege on. Normally, the content of these views is filtered based on the privileges of the user. CATALOG READ does not allow a user to view system views on which they have not been granted the SELECT privilege.



</td>
</tr>
<tr>
<td valign="top">

CERTIFICATE ADMIN



</td>
<td valign="top">

Authorizes the changing of certificates and certificate collections that are stored in the database.



</td>
</tr>
<tr>
<td valign="top">

CLIENT PARAMETER ADMIN



</td>
<td valign="top">

Authorizes a user to override the value of the CLIENT parameter for a database connection or to overwrite the value of the $$client$$ parameter in an SQL query.



</td>
</tr>
<tr>
<td valign="top">

CREATE JWT PROVIDER



</td>
<td valign="top">

Authorizes the creation of JWT providers by using the CREATE JWT PROVIDER statemen.



</td>
</tr>
<tr>
<td valign="top">

CREATE SAML PROVIDER



</td>
<td valign="top">

Authorizes the creation of SAML providers by using the CREATE SAML PROVIDER statement.



</td>
</tr>
<tr>
<td valign="top">

CREATE REMOTE SOURCE



</td>
<td valign="top">

Authorizes the creation of remote data sources by using the CREATE REMOTE SOURCE statement. It also allows you to set the purpose of a certificate collection to REMOTE SOURCE.



</td>
</tr>
<tr>
<td valign="top">

CREATE SCENARIO



</td>
<td valign="top">

Controls the creation of calculation scenarios and cubes \(calculation database\).



</td>
</tr>
<tr>
<td valign="top">

CREATE SCHEMA



</td>
<td valign="top">

Authorizes the creation of database schemas using the CREATE SCHEMA statement.



</td>
</tr>
<tr>
<td valign="top">

CREATE USERGROUP



</td>
<td valign="top">

Authorizes a user to create and drop a usergroup.



</td>
</tr>
<tr>
<td valign="top">

CREATE X509 PROVIDER



</td>
<td valign="top">

Authorizes the creation of X.509 providers by using the CREATE X509 PROVIDER statement.



</td>
</tr>
<tr>
<td valign="top">

CREDENTIAL ADMIN



</td>
<td valign="top">

Authorizes the use of the statements CREATE CREDENTIAL, ALTER CREDENTIAL, and DROP CREDENTIAL.



</td>
</tr>
<tr>
<td valign="top">

ENCRYPTION ROOT KEY ADMIN



</td>
<td valign="top">

Authorizes all statements related to management of root keys:

Allows access to the system views pertaining to encryption \(for example, ENCRYPTION\_ROOT\_KEYS, M\_ENCRYPTION\_OVERVIEW, M\_PERSISTENCE\_ENCRYPTION\_STATUS, M\_PERSISTENCE\_ENCRYPTION\_KEYS, and so on\).



</td>
</tr>
<tr>
<td valign="top">

EXPORT



</td>
<td valign="top">

The user must also have the SELECT privilege on the source tables to be exported. See the EXPORT statement for more information.



</td>
</tr>
<tr>
<td valign="top">

IMPORT



</td>
<td valign="top">

Authorizes the import activity in the database using the IMPORT statements. Additional privileges may also be required to be able to execute an IMPORT. See the IMPORT statement for more information.



</td>
</tr>
<tr>
<td valign="top">

INIFILE ADMIN



</td>
<td valign="top">

Authorizes making changes to system settings.



</td>
</tr>
<tr>
<td valign="top">

LDAP ADMIN



</td>
<td valign="top">

Authorizes the use of the CREATE | ALTER | DROP | VALIDATE LDAP PROVIDER statements.



</td>
</tr>
<tr>
<td valign="top">

LOG ADMIN



</td>
<td valign="top">

Authorizes the use of the ALTER SYSTEM LOGGING \[ON | OFF\] statements to enable or disable the log flush mechanism.



</td>
</tr>
<tr>
<td valign="top">

MONITOR ADMIN



</td>
<td valign="top">

Authorizes the use of the ALTER SYSTEM statements for events.



</td>
</tr>
<tr>
<td valign="top">

OPTIMIZER ADMIN



</td>
<td valign="top">

Authorizes the use of the ALTER SYSTEM statements concerning SQL PLAN CACHE and ALTER SYSTEM UPDATE STATISTICS statements, which influence the behavior of the query optimizer.



</td>
</tr>
<tr>
<td valign="top">

RESOURCE ADMIN



</td>
<td valign="top">

Authorizes statements concerning system resources \(for example, the ALTER SYSTEM RECLAIM DATAVOLUME and ALTER SYSTEM RESET MONITORING VIEW statements\). It also authorizes use of the Kernel Profiler statements, and many of the statements available in the Management Console.



</td>
</tr>
<tr>
<td valign="top">

SAVEPOINT ADMIN



</td>
<td valign="top">

Authorizes the execution of a savepoint using the ALTER SYSTEM SAVEPOINT statement.



</td>
</tr>
<tr>
<td valign="top">

SCENARIO ADMIN



</td>
<td valign="top">

Authorizes all calculation scenario-related activities \(including creation\).



</td>
</tr>
<tr>
<td valign="top">

SERVICE ADMIN



</td>
<td valign="top">

Authorizes the ALTER SYSTEM \[START|CANCEL|RECONFIGURE\] statements for administering system services of the database.



</td>
</tr>
<tr>
<td valign="top">

SESSION ADMIN



</td>
<td valign="top">

Authorizes the ALTER SYSTEM commands concerning sessions to stop or disconnect a user session or to change session variables.



</td>
</tr>
<tr>
<td valign="top">

SSL ADMIN



</td>
<td valign="top">

Authorizes the use of the SET...PURPOSE SSL statement. It also allows access to the PSES system view.



</td>
</tr>
<tr>
<td valign="top">

TABLE ADMIN



</td>
<td valign="top">

Authorizes LOAD, UNLOAD and MERGE of tables and table placement.



</td>
</tr>
<tr>
<td valign="top">

TRACE ADMIN



</td>
<td valign="top">

Authorizes the use of the ALTER SYSTEM statements related to database tracing \(including the Kernel Profiler feature\) and the changing of trace system settings.



</td>
</tr>
<tr>
<td valign="top">

TRUST ADMIN



</td>
<td valign="top">

Authorizes the use of statements to update the trust store.



</td>
</tr>
<tr>
<td valign="top">

WORKLOAD ADMIN



</td>
<td valign="top">

Authorizes execution of the workload class and mapping statements \(for example, CREATE | ALTER | DROP WORKLOAD CLASS, and CREATE | ALTER | DROP WORKLOAD MAPPING\).



</td>
</tr>
<tr>
<td valign="top">

WORKLOAD ANALYZE ADMIN



</td>
<td valign="top">

Used by the Analyze Workload, Capture Workload, and Replay Workload applications when performing workload analysis.



</td>
</tr>
<tr>
<td valign="top">

WORKLOAD CAPTURE ADMIN



</td>
<td valign="top">

Authorizes access to the monitoring view M\_WORKLOAD\_CAPTURES to see the current status of capturing and captured workloads, as well of execution of actions with the WORKLOAD\_CAPTURE procedure.



</td>
</tr>
<tr>
<td valign="top">

WORKLOAD REPLAY ADMIN



</td>
<td valign="top">

Authorizes access to the monitoring views M\_WORKLOAD\_REPLAY\_PREPROCESSES and M\_WORKLOAD\_REPLAYS to see current status of preprocessing, preprocessed, replaying, and replayed workloads, as well as the execution of actions with the WORKLOAD\_REPLAY procedure.



</td>
</tr>
<tr>
<td valign="top">

 *<identifier\>*.*<identifier\>* 



</td>
<td valign="top">

Components of the SAP HANA database can create new system privileges. These privileges use the component-name as the first identifier of the system privilege and the component-privilege-name as the second identifier.



</td>
</tr>
</table>



</dd><dt><b>

*<source\_privilege\>*

</b></dt>
<dd>

Restricts the access and modification of a source entry.

```
<source_privilege> ::= 
 CREATE VIRTUAL TABLE 
 | REMOTE TABLE ADMIN
 | REMOTE EXECUTE 
```


<dl>
<dt><b>

CREATE VIRTUAL TABLE

</b></dt>
<dd>

Authorizes the creation of proxy tables pointing to remote tables from the source entry.

Proxy tables are created in a schema and point to remote entries found in a source.



</dd><dt><b>

REMOTE EXECUTE

</b></dt>
<dd>

Authorizes the use of the REMOTE\_EXECUTE\_QUERY procedure on the specified remote sources.



</dd><dt><b>

REMOTE TABLE ADMIN

</b></dt>
<dd>

Authorizes the use of the WITH REMOTE clause when creating of a virtual table.



</dd>
</dl>



</dd><dt><b>

*<schema\_privilege\>*

</b></dt>
<dd>

Allows access to and modifications on a schema and the objects stored in the schema.

```
<schema_privilege> ::= 
 | ALL PRIVILEGES
 | ALTER 
 | CREATE ANY       
 | CREATE TEMPORARY TABLE
 | CREATE VIRTUAL PACKAGE 
 | DEBUG      
 | DEBUG MODIFY
 | DELETE       
 | DROP             
 | EXECUTE   
 | INDEX       
 | INSERT           
 | SELECT
 | SELECT METADATA   
 | TRIGGER 
 | UNMASKED     
 | UPDATE
```

The following schema privileges are defined:


<dl>
<dt><b>

ALL PRIVILEGES

</b></dt>
<dd>

Grants all existing schema privilege to *<grantee\>* with the exception of DEBUG, DEBUG MODIFY, and SQLSCRIPT LOGGING.

Additional privileges added later to the schema must be granted separately, or by executing another GRANT ALL PRIVILEGES statement.



</dd><dt><b>

ALTER

</b></dt>
<dd>

Allows the modification of all kinds of objects in a schema.



</dd><dt><b>

CREATE ANY

</b></dt>
<dd>

Allows the creation of all kinds of objects, such as tables, views, sequences, synonyms, triggers, SQLScript functions, graph workspaces, or database procedures, in a schema.



</dd><dt><b>

CREATE TEMPORARY TABLE

</b></dt>
<dd>

Allows you to create a temporary local table, which can be used as input for procedures, even if the user does not have the CREATE ANY privilege for the corresponding schema.



</dd><dt><b>

CREATE VIRTUAL PACKAGE

</b></dt>
<dd>

Allows creation of virtual packages for objects, such as functions and procedures, that can be run on remote sources.



</dd><dt><b>

DELETE, DROP, EXECUTE, INDEX, INSERT, SELECT, UPDATE

</b></dt>
<dd>

The specified privilege is granted on every object stored in the specified schema currently and going forward. For detailed descriptions of the privileges, including which privileges are applicable to different objects, see the table describing object privileges.



</dd><dt><b>

DEBUG

</b></dt>
<dd>

Allows the use of debug features.



</dd><dt><b>

DEBUG MODIFY

</b></dt>
<dd>

For internal use only.



</dd><dt><b>

SELECT METADATA

</b></dt>
<dd>

Allows the selection of metadata for one schema from the catalog. This privilege includes access to the object definition in the case of a view, procedure, function, or trigger that may be located in different schemas.



</dd><dt><b>

TRIGGER

</b></dt>
<dd>

Allows you to create, alter, drop, enable, and disable triggers.



</dd><dt><b>

UNMASKED

</b></dt>
<dd>

Authorizes access to masked and anonymized data in tables and user-defined views. This privilege is required to view the original data in views and tables that are defined with the WITH MASK clause or the original data in views that have been anonymized.



</dd>
</dl>



</dd><dt><b>

*<object\_privilege\>*

</b></dt>
<dd>

Restricts access to, and modification of, database objects.

```
<object_privilege> ::= 
 ALL PRIVILEGES   
 | ALTER
 | CREATE ANY
 | CREATE VIRTUAL FUNCTION
 | CREATE VIRTUAL PACKAGE
 | CREATE VIRTUAL PROCEDURE
 | CREATE VIRTUAL TABLE
 | DEBUG          
 | DEBUG MODIFY
 | DELETE 
 | DROP           
 | EXECUTE 
 | INDEX          
 | INSERT 
 | REFERENCES
 | SELECT
 | SELECT METADATA
 | TRIGGER        
 | REMOTE TABLE ADMIN
 | UNMASKED
 | UPDATE         
 | USERGROUP OPERATOR
 | <identifier>.<identifier>
```

For synonyms, the same restrictions apply to the synonym as they do for the object that the synonym represents.

The following table describes the supported object privileges in an SAP HANA database.


<table>
<tr>
<th valign="top">

Object Privilege



</th>
<th valign="top">

Command Types



</th>
<th valign="top">

Applies to



</th>
<th valign="top">

Privilege Description



</th>
</tr>
<tr>
<td valign="top">

ALL PRIVILEGES



</td>
<td valign="top">

DDL & DML



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views



</td>
<td valign="top">

This privilege is a collection of all Data Definition Language \(DDL\) and Data Manipulation Language \(DML\) privileges that the grantor currently possesses and is allowed to grant further. The privilege it grants is specific to the particular object being acted upon.

This privilege collection is dynamically evaluated for the given grantor and object.



</td>
</tr>
<tr>
<td valign="top">

ALTER



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views
-   Functions/procedures
-   JWT, SAML, and X509 providers
-   PSEs



</td>
<td valign="top">

Authorizes the ALTER statement for the object.

When granting ALTER on a JWT, SAML, or X509 provider, you must include the keywords JWT/SAML/X509 PROVIDER before the name of the provider \(for example: <code>GRANT ALTER ON <b>JWT PROVIDER</b> <i class="varname">&lt;provider_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\).

When granting ALTER on a PSE, you must include the keyword PSE before the name of the PSE \(for example: <code>GRANT ALTER ON <b>PSE</b> <i class="varname">&lt;pse_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\).



</td>
</tr>
<tr>
<td valign="top">

CREATE ANY



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views
-   Sequences
-   Functions/procedures
-   Remote sources
-   Graph workspaces
-   Triggers



</td>
<td valign="top">

Authorizes all CREATE statements for the object.



</td>
</tr>
<tr>
<td valign="top">

CREATE VIRTUAL FUNCTION



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Remote sources



</td>
<td valign="top">

Authorizes creation of virtual functions \(the REFERENCES privilege is also required\).



</td>
</tr>
<tr>
<td valign="top">

CREATE VIRTUAL PROCEDURE



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Remote sources



</td>
<td valign="top">

Authorizes creation of virtual procedure to create and run procedures on a remote source.



</td>
</tr>
<tr>
<td valign="top">

CREATE VIRTUAL PACKAGE



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas



</td>
<td valign="top">

Authorizes creation of virtual packages that can be run on remote sources.



</td>
</tr>
<tr>
<td valign="top">

CREATE VIRTUAL TABLE



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Remote sources



</td>
<td valign="top">

Authorizes the creation of proxy tables pointing to remote tables from the source entry.



</td>
</tr>
<tr>
<td valign="top">

CREATE TEMPORARY TABLE



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas



</td>
<td valign="top">

Authorizes the creation of a temporary local table, which can be used as input for procedures, even if the user does not have the CREATE ANY privilege for the schema.



</td>
</tr>
<tr>
<td valign="top">

DEBUG



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Calculation Views
-   Functions/procedures



</td>
<td valign="top">

Authorizes debug functionality for the procedure or calculation view or for the procedures and calculation views of a schema.



</td>
</tr>
<tr>
<td valign="top">

DEBUG MODIFY



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Functions/procedures



</td>
<td valign="top">

For internal use only.



</td>
</tr>
<tr>
<td valign="top">

DELETE



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views
-   Functions/procedures



</td>
<td valign="top">

Authorizes the DELETE and TRUNCATE statements for the object.

While DELETE applies to views, it only applies to updatable views \(that is, views that do not use a join, do not contain a UNION, and do not use aggregation\).



</td>
</tr>
<tr>
<td valign="top">

DROP



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views
-   Sequences
-   Functions/procedures
-   Remote sources
-   Graph workspaces
-   JWT, SAML, and X509 providers
-   PSEs



</td>
<td valign="top">

Authorizes the DROP statements for the object.

When granting DROP on a JWT, SAML, or X509 provider, you must include the keywords JWT/SAML/X509 PROVIDER before the name of the provider \(for example: <code>GRANT DROP ON <b>JWT PROVIDER</b> <i class="varname">&lt;provider_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\).

When granting DROP on a PSE, you must include the keyword PSE before the name of the PSE \(for example: <code>GRANT DROP ON <b>PSE</b> <i class="varname">&lt;pse_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\).



</td>
</tr>
<tr>
<td valign="top">

EXECUTE



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Functions/procedures



</td>
<td valign="top">

Authorizes the execution of a SQLScript function or a database procedure by using the CALLS or CALL statement respectively. It also allows a user to execute a virtual function.



</td>
</tr>
<tr>
<td valign="top">

INDEX



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas
-   Tables



</td>
<td valign="top">

Authorizes the creation, modification, or dropping of indexes for the object.



</td>
</tr>
<tr>
<td valign="top">

INSERT



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views



</td>
<td valign="top">

Authorizes the INSERT statement for the object.

The INSERT and UPDATE privilege are both required on the object to allow the REPLACE and UPSERT statements to be used.

While INSERT applies to views, it only applies to updatable views \(views that do not use a join, do not contain a UNION, and do not use aggregation\).



</td>
</tr>
<tr>
<td valign="top">

REFERENCES



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas
-   Tables
-   JWT, SAML, and X509 providers
-   PSEs



</td>
<td valign="top">

Authorizes the usage of all tables in this schema or this table in a foreign key definition, or the usage of a personal security environment \(PSE\). It also allows a user to reference a virtual function package.

When granting REFERENCES on a JWT, SAML, or X509 provider, you must include the keywords JWT/SAML/X509 PROVIDER before the name of the provider \(for example: <code>GRANT REFERENCES ON <b>JWT PROVIDER</b> <i class="varname">&lt;provider_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\).

When granting REFERENCES on a PSE, you must include the keyword PSE before the name of the PSE \(for example: <code>GRANT REFERENCES ON <b>PSE</b> <i class="varname">&lt;pse_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\).



</td>
</tr>
<tr>
<td valign="top">

REMOTE TABLE ADMIN



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Remote sources



</td>
<td valign="top">

Authorizes the creation of tables on a remote source object.



</td>
</tr>
<tr>
<td valign="top">

SELECT



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views
-   Sequences
-   Graph workspaces



</td>
<td valign="top">

Authorizes the SELECT statement for the object or the usage of a sequence. When selection from system-versioned tables, users must have SELECT on both the table and its associated history table.



</td>
</tr>
<tr>
<td valign="top">

SELECT METADATA



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Tables



</td>
<td valign="top">

Authorizes access to the complete metadata of all objects in a schema \(including procedure and view definitions\), including objects that may be located in other schemas.



</td>
</tr>
<tr>
<td valign="top">

TRIGGER



</td>
<td valign="top">

DDL



</td>
<td valign="top">

-   Schemas
-   Tables



</td>
<td valign="top">

Authorizes the CREATE/ALTER/DROP/ENABLE and DISABLE TRIGGER statements for the specified table or the tables in the specified schema.



</td>
</tr>
<tr>
<td valign="top">

UNMASKED



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Views
-   Tables



</td>
<td valign="top">

Authorizes access to masked and anonymized data in user-defined views and tables. This privilege is required to view the original data in views and tables that are defined by using the WITH MASK clause or the original data in views that have been anonymized.



</td>
</tr>
<tr>
<td valign="top">

UPDATE



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Schemas
-   Tables
-   Views



</td>
<td valign="top">

While UPDATE applies to views, it only applies to updatable views \(views that do not use a join, do not contain a UNION, and do not use aggregation\).



</td>
</tr>
<tr>
<td valign="top">

USERGROUP OPERATOR



</td>
<td valign="top">

DML



</td>
<td valign="top">

-   Usergroups



</td>
<td valign="top">

Authorizes a user to change the settings for a usergroup, and to add and remove users to/from a usergroup.

Users with the USERGROUP OPERATOR privilege can also create and drop users, but only within the usergroup they have the USERGROUP OPERATOR privilege on \(CREATE USER *<user\_name\>* SET USERGROUP *<usergroup\_name\>*\).

A user can have the USERGROUP OPERATOR privilege on more than one usergroup, and a usergroup can have more than one user with the USERGROUP OPERATOR privilege on it.

When granting USERGROUP OPERATOR, you must include the keyword USERGROUP before the name of the usergroup \(for example: <code>GRANT USERGROUP OPERATOR ON <b>USERGROUP</b> <i class="varname">&lt;usergroup_name&gt;</i> TO <i class="varname">&lt;grantee&gt;</i></code>\). This is slightly different syntax than granting other object privileges.



</td>
</tr>
<tr>
<td valign="top">

 *<identifier\>*.*<identifier\>* 



</td>
<td valign="top">

DDL



</td>
<td valign="top">

 



</td>
<td valign="top">

Components of the SAP HANA database can create new object privileges. These privileges use the component-name as first identifier of the system privilege and the component-privilege-name as the second identifier.



</td>
</tr>
</table>



</dd><dt><b>

*<hana\_object\_name\>*

</b></dt>
<dd>

```
<hana_object_name> ::= 
 <table_name> 
 | <view_name>
 | <sequence_name> 
 | <procedure_name>
 | <synonym_name>
```

```
<table_name> ::= [<schema_name>.]<identifier>
```

```
<view_name> ::= [<schema_name>.]<identifier>
```

```
<sequence_name> ::= [<schema_name>.]<identifier>
```

```
<procedure_name> ::= [<schema_name>.]<identifier>
```

```
<synonym_name> ::= [<schema_name>.]<identifier>
```



</dd><dt><b>

*<schema\_privilege\>*

</b></dt>
<dd>

Allows access to and modifications on a schema and the objects stored in the schema.


<dl>
<dt><b>

ALTER

</b></dt>
<dd>

Authorizes the ALTER statement for all objects in the schema.



</dd><dt><b>

CREATE ANY

</b></dt>
<dd>

Authorizes all CREATE statements for all objects in the schema.



</dd><dt><b>

DELETE

</b></dt>
<dd>

Authorizes the DELETE and TRUNCATE statements for all objects in the schema.



</dd><dt><b>

DROP

</b></dt>
<dd>

Authorizes the DROP statements for all objects in the schema.



</dd><dt><b>

INSERT

</b></dt>
<dd>

Authorizes the INSERT statements for all objects in the schema.



</dd><dt><b>

SELECT

</b></dt>
<dd>

Authorizes the SELECT statements for all objects in the schema.



</dd><dt><b>

UPDATE

</b></dt>
<dd>

Authorizes the UPDATE statements for all objects in the schema.



</dd>
</dl>



</dd><dt><b>

CREATE VIRTUAL TABLE

</b></dt>
<dd>

Authorizes the creation of proxy tables pointing to remote tables from the source entry. Proxy tables are created in a schema and point to remote entries found in a source.



</dd><dt><b>

REMOTE TABLE ADMIN

</b></dt>
<dd>

Authorizes the creation of tables on a remote source object.



</dd><dt><b>

EXECUTE

</b></dt>
<dd>

Allows the creation of data lake Relational Engine tables, views, system views, and indexes using the REMOTE\_EXECUTE procedure for the container *<relational\_container\_name\>*.



</dd><dt><b>

WITH ADMIN OPTION and WITH GRANT OPTION

</b></dt>
<dd>

Specifies that the granted privileges can be granted further by the specified user or by users with the specified role.



</dd>
</dl>



<a name="loioee1648d43b994f44b457a1dba6072442__sql_grant_1sql_grant_description"/>

## Description

This syntax is specific to granting SAP HANA database privileges in a data lake Relational Engine context. For a full listing of available privileges, see the *GRANTING Statement \(Access Control\)* in the *SAP HANA Cloud, SAP HANA Database SQL Reference Guide*.



<a name="loioee1648d43b994f44b457a1dba6072442__section_o5s_n4x_4bb"/>

## Permissions

To use the GRANT statement to grant privileges to other users and roles, a user must have the privilege and also the permissions required to grant that privilege.

**DBADMIN \(cloud super-user\), non-RESTRICTED users, and RESTRICTED users**: A DBADMIN user has all system privileges and the role PUBLIC. However, a DBADMIN user can’t select or change data in another user's tables unless this privilege has been explicitly granted. A non-RESTRICTED user has the PUBLIC role, has the privileges required to create objects in their own default schema, and can grant privileges on their objects to other users and roles. A RESTRICTED user doesn’t have the PUBLIC role and can’t create objects in their own schemas. RESTRICTED users have only the privileges that have been explicitly granted to them. For more information on SAP HANA database users, see *Managing SAP HANA Database Users* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.

Users can’t grant privileges to themselves.

For objects that are dependent on other objects, like views being dependent on tables, there could be times when the schema of the dependent object doesn’t have a complete set of privileges. This situation can occur if the user doesn’t have privileges on the underlying objects on which their object depends.



<a name="loioee1648d43b994f44b457a1dba6072442__sql_grant_1sql_grant_examples"/>

## Examples

Grant the INSERT and DELETE privileges for the table V\_T1 in schema SYSHDL\_CONTAINER1 to USER1.

```
GRANT INSERT, DELETE ON SYSHDL_CONTAINER1.V_T1 TO USER1;
```

Grant the role ROLE1 to USER1.

```
GRANT ROLE1 TO USER1 WITH ADMIN OPTION;
```

Grant the EXECUTE privilege for the REMOTE\_EXECUTE procedure for container SYSHDL\_CONTAINER1 to USER1 with the ability to further grant the privilege to other users or roles.

```
GRANT EXECUTE ON SYSHDL_CONTAINER1.REMOTE_EXECUTE TO USER1 WITH GRANT OPTION;
```

Grant the SELECT privilege on the SAP HANA database schema SYSHDL\_CONTAINER1 to USER1.

```
GRANT SELECT ON SCHEMA SYSHDL_CONTAINER1 TO USER1;
```

Grant the CATALOG READ privilege to USER1 with the ability to further grant the privilege to other users or roles.

```
GRANT CATALOG READ TO USER1 WITH ADMIN OPTION;
```

Grant the REMOTE EXECUTE privilege on the remote source SYSHDL\_CONTAINER1\_SOURCE to USER1.

```
GRANT REMOTE EXECUTE ON REMOTE SOURCE SYSHDL_CONTAINER1_SOURCE TO USER1;
```

**Related Information**  


[REVOKE Statement for SAP HANA Database](revoke-statement-for-sap-hana-database-1ef5b72.md "Revoke privileges from users and roles to remove the ability to manage and query data lake Relational Engine data.")

[SAP HANA Cloud, SAP HANA Database SQL Reference Guide](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/2021_01_QRC/en-US)

[SAP HANA Cloud, SAP HANA Database Administration Guide](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2021_01_QRC/en-US/ed7af17e5ae14de694d9bee5f35098f4.html)

