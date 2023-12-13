<!-- loiofd99ac0ce9914c7695488ca4b2fa70f5 -->

# REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements

To run data lake Relational Engine SQL statements using the SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_DDL procedure, you embed the SQL syntax within the procedure.



You must be connected to an SAP HANA database integrated with data lake Relational Engine \(also referred to as data lake Relational Engine \(SAP HANA DB-Managed\)\) as an SAP HANA database user to run REMOTE\_EXECUTE or REMOTE\_EXECUTE\_DDL.

To use REMOTE\_EXECUTE or REMOTE\_EXECUTE\_DDL requires one of the following:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   To run either REMOTE\_EXECUTE or REMOTE\_EXECUTE\_DDL requires EXECUTE permission on the SAP HANA database procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

    > ### Note:  
    > When processing the syntax embedded within the procedure, REMOTE\_EXECUTE connects directly to the data lake Relational Engine **writer** node, while REMOTE\_EXECUTE\_DDL connects directly to the data lake Relational Engine **coordinator** node.




When executing an SQL statement using the REMOTE\_EXECUTE procedure, you preface the name of the procedure with the name of the relational container the statement is being run against. You then enclose the SQL statement withing brackets, beginning and ending the syntax with a single quotation mark. For example, to create a table in the relational container SYSHDL\_CONTAINER1, execute:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE ('
   CREATE TABLE T1 (COL1 VARCHAR(10), COL2 VARCHAR(10), COL3 INT)
   ');
```

If the SQL statement contains a reference to an object that resides in the default relational container schema \(*<default\_relational\_container\_schema\_name\>*\), then you don't need to specify the schema name in the SQL Statement. But if the object resides in a user-defined relational container schema, you must preface the name of the object with the name of the user-defined schema.

For example, to create table T2 in relational container schema MYSCHEMA, in relational container SYSHDL\_CONTAINER1, execute:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE ('
   CREATE TABLE SYSHDL_CONTAINER1_MYSCHEMA.T2 (COL1 VARCHAR(10), COL2 VARCHAR(10), COL3 INT)
   ');
```

If syntax within the SQL statement contains single quotes, then the quoted syntax must itself be enclosed in single quotes. For example, '<syntax\>' becomes ''<syntax\>''.

For example, this INSERT statement inserts a quoted text value into the DepartmentName column. Therefore, the value must itself be enclosed in single quotes. To run this INSERT statement, execute:

```
CALL SYSHDL_CONTAINER1.REMOTE_EXECUTE ('
   INSERT INTO DEPARTMENTS (DepartmentID, DepartmentName, DepartmentHeadID)
   VALUES (600, ''Eastern Sales'', 501)
   ');
```

