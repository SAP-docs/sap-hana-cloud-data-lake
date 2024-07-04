<!-- loioa449325c84f21015a04a8ed51049a5a5 -->

# Alphabetical List of System Privileges for Data Lake Relational Engine

A list of all available system privileges.



System privileges control the rights of users to perform authorized database tasks.




<table>
<tr>
<th valign="top">

System Privilege

</th>
<th valign="top">

Allows a User To...

</th>
</tr>
<tr>
<td valign="top">

ALTER ANY INDEX

</td>
<td valign="top">

Alter and comment on indexes on tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

ALTER ANY MATERIALIZED VIEW

</td>
<td valign="top">

Alter and comment on materialized views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

ALTER ANY OBJECT

</td>
<td valign="top">

Alter and comment on the following types of objects owned by any user:

-   Data types
-   Events
-   Functions
-   Indexes
-   Materialized views
-   Messages
-   Procedures
-   Sequence generators
-   Statistics
-   Tables
-   Text indexes
-   Triggers
-   Views



</td>
</tr>
<tr>
<td valign="top">

ALTER ANY PROCEDURE

</td>
<td valign="top">

Alter and comment on procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

ALTER ANY SEQUENCE

</td>
<td valign="top">

Alter sequence generators owned by any user.

</td>
</tr>
<tr>
<td valign="top">

ALTER ANY TABLE

</td>
<td valign="top">

-   Alter sequence generators owned by anyAlter and comment on tables \(including proxy tables\) owned by any user.
-   Truncate tables, table partitions, or views owned by any user.
-   Comment on tables \(including proxy tables\) and columns in tables owned by any user.



</td>
</tr>
<tr>
<td valign="top">

ALTER ANY TEXT CONFIGURATION

</td>
<td valign="top">

Alter and comment on text configuration objects owned by any user.

</td>
</tr>
<tr>
<td valign="top">

ALTER ANY TRIGGER

</td>
<td valign="top">

-   Alter triggers on tables and views.
-   Issue comments on tables \(also requires the ALTER object-level privilege on the table\).



</td>
</tr>
<tr>
<td valign="top">

ALTER ANY VIEW

</td>
<td valign="top">

Alter and comment on views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

ALTER DATATYPE

</td>
<td valign="top">

Alter data types.

</td>
</tr>
<tr>
<td valign="top">

ALTER TABLE FILES SERVICE

</td>
<td valign="top">

Alter an external catalog table and add or drop a datasource in SQL on Files.

</td>
</tr>
<tr>
<td valign="top">

BACKUP ANY TABLE

</td>
<td valign="top">

Back up a table.

</td>
</tr>
<tr>
<td valign="top">

BACKUP OWNER TABLE

</td>
<td valign="top">

Back up self-owned tables.

</td>
</tr>
<tr>
<td valign="top">

CHANGE PASSWORD

</td>
<td valign="top">

Manage user passwords for any user. This system privilege can apply to all users, or it can be limited to a set of specified users, or users who are granted one or more specified roles.This system privilege is not required to change a user's own password.

</td>
</tr>
<tr>
<td valign="top">

CHECKPOINT

</td>
<td valign="top">

Force the database server to execute a checkpoint.

</td>
</tr>
<tr>
<td valign="top">

COMMENT ANY OBJECT

</td>
<td valign="top">

Allows a user to comment on any type of object owned by any user that can be created using the CREATE ANY OBJECT system privilege.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY INDEX

</td>
<td valign="top">

Create and comment on indexes and text indexes on tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY MATERIALIZED VIEW

</td>
<td valign="top">

Create and comment on materialized views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY MUTEX SEMAPHORE

</td>
<td valign="top">

Create a mutex or semaphore owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY OBJECT

</td>
<td valign="top">

Create and comment on the following types of objects owned by any user:

-   Data types
-   Events
-   Functions
-   Indexes
-   Materialized views
-   Messages
-   Procedures
-   Sequence generators
-   Statistics
-   Tables
-   Text configuration objects
-   Text indexes
-   Triggers
-   Views



</td>
</tr>
<tr>
<td valign="top">

CREATE ANY PROCEDURE

</td>
<td valign="top">

Create and comment on procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY DATABASE SCHEMA

</td>
<td valign="top">

Create any schema.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY SEQUENCE

</td>
<td valign="top">

Create sequence generators, regardless of owner.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY TABLE

</td>
<td valign="top">

Create and comment on tables \(including proxy tables\) owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY TEXT CONFIGURATION

</td>
<td valign="top">

Alter and comment on text configuration objects owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY TRIGGER

</td>
<td valign="top">

Create and comment \(also requires the ALTER object level privilege on the table\) on tables and views.

</td>
</tr>
<tr>
<td valign="top">

CREATE ANY VIEW

</td>
<td valign="top">

Create and comment on views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

CREATE DATABASE SCHEMA

</td>
<td valign="top">

Create self-owned schemas.

</td>
</tr>
<tr>
<td valign="top">

CREATE DATABASE VARIABLE

</td>
<td valign="top">

Create, select from, and update self-owned database-scope variables.

</td>
</tr>
<tr>
<td valign="top">

CREATE DATATYPE

</td>
<td valign="top">

Create data types.

</td>
</tr>
<tr>
<td valign="top">

CREATE EXTERNAL REFERENCE

</td>
<td valign="top">

Create external references in the database. You need the system privileges required to create specific database objects before you can create external references. For example, creating a self-owned text configuration object that uses an external term breaker requires both the CREATE TEXT CONFIGURATION and CREATE EXTERNAL REFERENCE system privileges.

</td>
</tr>
<tr>
<td valign="top">

CREATE MATERIALIZED VIEW

</td>
<td valign="top">

Create and comment on self-owned materialized views.

</td>
</tr>
<tr>
<td valign="top">

CREATE MESSAGE

</td>
<td valign="top">

Create messages.

</td>
</tr>
<tr>
<td valign="top">

CREATE PROCEDURE

</td>
<td valign="top">

Create and comment on self-owned procedures and functions.

</td>
</tr>
<tr>
<td valign="top">

CREATE PROXY TABLE

</td>
<td valign="top">

Create self-owned proxy tables.

</td>
</tr>
<tr>
<td valign="top">

CREATE SCHEMA FILES SERVICE

</td>
<td valign="top">

Create an external catalog schema in SQL on Files.

</td>
</tr>
<tr>
<td valign="top">

CREATE TABLE

</td>
<td valign="top">

-   Create self-owned tables.
-   Comment on self-owned columns and tables.



</td>
</tr>
<tr>
<td valign="top">

CREATE TABLE FILES SERVICE

</td>
<td valign="top">

Create an external catalog table in SQL on Files.

</td>
</tr>
<tr>
<td valign="top">

CREATE TEXT CONFIGURATION

</td>
<td valign="top">

Create and comment on self-owned text configuration objects.

</td>
</tr>
<tr>
<td valign="top">

CREATE VIEW

</td>
<td valign="top">

Create and comment on self-owned views. Required to create self-owned views.

</td>
</tr>
<tr>
<td valign="top">

DEBUG ANY PROCEDURE

</td>
<td valign="top">

Debug any database object.

</td>
</tr>
<tr>
<td valign="top">

DELETE ANY TABLE

</td>
<td valign="top">

Delete rows in tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY DATABASE SCHEMA

</td>
<td valign="top">

Drop any schema.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY INDEX

</td>
<td valign="top">

Drop indexes and text indexes on tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY MATERIALIZED VIEW

</td>
<td valign="top">

Drop materialized views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY MUTEX SEMAPHORE

</td>
<td valign="top">

Drop a mutex or semaphore owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY OBJECT

</td>
<td valign="top">

Drop the following types of objects owned by any user:

-   Data types
-   Events
-   Functions
-   Indexes
-   Materialized views
-   Messages
-   Procedures
-   Sequence generators
-   Statistics
-   Tables
-   Text configuration objects
-   Triggers
-   Views



</td>
</tr>
<tr>
<td valign="top">

DROP ANY PROCEDURE

</td>
<td valign="top">

Drop procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY SEQUENCE

</td>
<td valign="top">

Drop sequence generators owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY TABLE

</td>
<td valign="top">

Drop tables \(including proxy tables\) owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY TEXT CONFIGURATION

</td>
<td valign="top">

Drop text configuration objects owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY VIEW

</td>
<td valign="top">

Drop views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

DROP ANY CONNECTION

</td>
<td valign="top">

Drop any connections to the database.

</td>
</tr>
<tr>
<td valign="top">

DROP DATATYPE

</td>
<td valign="top">

Drop data types.

</td>
</tr>
<tr>
<td valign="top">

DROP MESSAGE

</td>
<td valign="top">

Drop messages.

</td>
</tr>
<tr>
<td valign="top">

DROP SCHEMA FILES SERVICE

</td>
<td valign="top">

Drop an external catalog schema in SQL on Files.

</td>
</tr>
<tr>
<td valign="top">

DROP TABLE FILES SERVICE

</td>
<td valign="top">

Drop an external catalog table in SQL on Files.

</td>
</tr>
<tr>
<td valign="top">

EXECUTE ANY PROCEDURE

</td>
<td valign="top">

Execute procedures and functions owned by any user.

</td>
</tr>
<tr>
<td valign="top">

INSERT ANY TABLE

</td>
<td valign="top">

Insert rows into tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

LOAD ANY TABLE

</td>
<td valign="top">

Load data into tables owned by any user.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY DATABASE VARIABLE

</td>
<td valign="top">

Create database-scope variables owned by yourself or by PUBLIC.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY DBSPACE

</td>
<td valign="top">

Run select system stored procedures to manage the instance.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY EVENT

</td>
<td valign="top">

Create, alter, drop, trigger, and comment on any event in the database.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY LDAP SERVER

</td>
<td valign="top">

Create, alter, drop, validate, and comment on LDAP servers.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY LOGIN POLICY

</td>
<td valign="top">

Create, alter, drop, and comment on login policies.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY OBJECT PRIVILEGE

</td>
<td valign="top">

-   Grant and revoke SELECT, INSERT, DELETE, UPDATE, ALTER, REFERENCES, LOAD, and TRUNCATE object-level privileges on tables owned by any user.
-   Grant and revoke SELECT, INSERT, DELETE, and UPDATE object-level privileges on views owned by any user.
-   Grant and revoke EXECUTE privileges on procedures and functions owned by any user.
-   Grant and revoke USAGE object-level privileges on sequence generators owned by any user.



</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY OLD TABLE VERSION

</td>
<td valign="top">

Unpin any pin requests.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY REMOTE SERVER

</td>
<td valign="top">

Create, alter, and drop SERVER objects.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY STATISTICS

</td>
<td valign="top">

Create, alter, drop, and update database statistics for any table.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY TRACE SESSION

</td>
<td valign="top">

Create a trace session.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ANY USER

</td>
<td valign="top">

-   Create, alter, drop, and comment on database users \(including assigning an initial password\).
-   Force a password change on next login for any user.
-   Assign and reset the login policy for any user.



</td>
</tr>
<tr>
<td valign="top">

MANAGE AUDITING

</td>
<td valign="top">

Run the sa\_audit\_string stored procedure.

</td>
</tr>
<tr>
<td valign="top">

MANAGE CERTIFICATES

</td>
<td valign="top">

Manage audit and database sessions.

</td>
</tr>
<tr>
<td valign="top">

MANAGE CREDENTIAL

</td>
<td valign="top">

Create and drop credentials for any credential user.

</td>
</tr>
<tr>
<td valign="top">

MANAGE EVENT

</td>
<td valign="top">

Create, alter, drop, trigger, and comment on events owned by self.

</td>
</tr>
<tr>
<td valign="top">

MANAGE OLD TABLE VERSION

</td>
<td valign="top">

Unpin only the requests created by self.

</td>
</tr>
<tr>
<td valign="top">

MANAGE OWNER CERTIFICATES

</td>
<td valign="top">

Manage self-owned certificates.

</td>
</tr>
<tr>
<td valign="top">

MANAGE PROFILING

</td>
<td valign="top">

Manage database server tracing. The DIAGNOSTICS system role is also required to fully utilize diagnostics functionality for user information.

</td>
</tr>
<tr>
<td valign="top">

MANAGE ROLES

</td>
<td valign="top">

Create new roles and act as a global administrator for new and existing roles. By default, MANAGE ROLES is granted administrative rights on each newly created role. A user requires administrative rights on the role to delete it.

You can grant users administration of a role while or after you create that role. When you grant it directly to a user, the user does not require the MANAGE ROLES system privilege to administer the role.

If you do not specify a role administrator during role creation, the MANAGE ROLES system privilege is automatically granted to the role with the ADMIN ONLY OPTION clause, allowing the global role administrator to administer the role. If at least one role administrator is specified during creation, the MANAGE ROLES system privilege is not granted to the role, and global role administrators cannot manage the role.

</td>
</tr>
<tr>
<td valign="top">

MANAGE TRUST

</td>
<td valign="top">

Authorizes a user to create and drop a PSE.

</td>
</tr>
<tr>
<td valign="top">

MONITOR

</td>
<td valign="top">

Monitor a database, including accessing privileged statistics, connected users, and locks.

</td>
</tr>
<tr>
<td valign="top">

NOTIFY TRACE EVENT

</td>
<td valign="top">

Notify an event.

</td>
</tr>
<tr>
<td valign="top">

READ CLIENT FILE

</td>
<td valign="top">

Read files on the client computer.

</td>
</tr>
<tr>
<td valign="top">

READ FILE

</td>
<td valign="top">

Read files on the database server computer.

</td>
</tr>
<tr>
<td valign="top">

REORGANIZE ANY OBJECT

</td>
<td valign="top">

Reorganize tables and materialized views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

RESTORE ANY TABLE

</td>
<td valign="top">

Restore any table.

</td>
</tr>
<tr>
<td valign="top">

RESTORE OWNER TABLE

</td>
<td valign="top">

Restore self-owned tables.

</td>
</tr>
<tr>
<td valign="top">

SELECT ANY TABLE

</td>
<td valign="top">

Query tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

SELECT PUBLIC DATABASE VARIABLE

</td>
<td valign="top">

Select the value of a database-scope variable owned by PUBLIC.

</td>
</tr>
<tr>
<td valign="top">

SET ANY CUSTOMER PUBLIC OPTION

</td>
<td valign="top">

Set PUBLIC database options that have the customer bit set and that do not require the SET ANY SECURITY CUSTOMER OPTION or the SET ANY CUSTOMER SYSTEM OPTION system privileges.

</td>
</tr>
<tr>
<td valign="top">

SET ANY CUSTOMER SECURITY OPTION

</td>
<td valign="top">

Set any CUSTOMER PUBLIC security database options that have the customer bit set.

</td>
</tr>
<tr>
<td valign="top">

SET ANY CUSTOMER SYSTEM OPTION

</td>
<td valign="top">

Set CUSTOMER PUBLIC system database options that have the customer bit set.

</td>
</tr>
<tr>
<td valign="top">

SET ANY USER DEFINED OPTION

</td>
<td valign="top">

Set user-defined database options.

</td>
</tr>
<tr>
<td valign="top">

TRUNCATE ANY TABLE

</td>
<td valign="top">

Truncate data for tables and materialized views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

UPDATE ANY MUTEX SEMAPHORE

</td>
<td valign="top">

Update a mutex or semaphore owned by any user.

</td>
</tr>
<tr>
<td valign="top">

UPDATE ANY TABLE

</td>
<td valign="top">

Update rows in tables and views owned by any user.

</td>
</tr>
<tr>
<td valign="top">

UPDATE PUBLIC DATABASE VARIABLE

</td>
<td valign="top">

Update database-scope variables owned by PUBLIC.

</td>
</tr>
<tr>
<td valign="top">

USE ANY SEQUENCE

</td>
<td valign="top">

Use sequence generators owned by any user.

</td>
</tr>
<tr>
<td valign="top">

VALIDATE ANY OBJECT

</td>
<td valign="top">

Validate tables, materialized views, and indexes owned by any user.

</td>
</tr>
<tr>
<td valign="top">

WRITE CLIENT FILE

</td>
<td valign="top">

Write files to the client computer.

</td>
</tr>
<tr>
<td valign="top">

WRITE FILE

</td>
<td valign="top">

Write files on the database server computer.

</td>
</tr>
</table>

