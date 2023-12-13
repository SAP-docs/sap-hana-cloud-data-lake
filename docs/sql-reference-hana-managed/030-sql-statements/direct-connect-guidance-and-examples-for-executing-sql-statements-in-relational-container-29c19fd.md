<!-- loio29c19fdbc66e4288b9b670877246334d -->

# Direct Connect Guidance and Examples for Executing SQL Statements in Relational Containers

To run data lake Relational Engine SQL statements when directly connected to a data lake Relational Engine integrated withSAP HANA database, you must have permissions to the access the data lake Relational Engine relational container impacted by the SQL statement.



In addition, you must have the required privileges to execute the data lake Relational Engine SQL statement.

When directly connected, you don't need to use the SAP HANA database REMOTE\_EXECUTE procedure.

When the SQL statement references an object in a relational container, you must preface the object name with the relational container schema name, either the default schema name \(SYSHDL\_*<relational\_container\_name\>*\) or the user-defined schema name \(SYSHDL\_*<relational\_container\_name\>*\_*<schema-name\>*\).

For example, to insert data into table T1 in default schema in relational container SYSHDL\_CONTAINER1, execute:

```
INSERT INTO SYSHDL_CONTAINER1.T1 (COL1, COL2) 
   VALUES (1,2);
```

To insert data into table T2 in user-defined schema MYSCHEMA in relational container SYSHDL\_CONTAINER1, execute:

```
INSERT INTO SYSHDL_CONTAINER1_MYSCHEAM.T2 (COL1, COL2) 
   VALUES (1,2);
```

When directly connected, even if you have the required data lake Relational Engine privileges to create, alter, or drop objects, you cannot execute these types of SQL statements against objects in the default relational container schema \(SYSHDL\_*<relational\_container\_name\>*\). A permissions error is returned when you try. Objects can only be created in the default relational container schema using the REMOTE\_EXECUTE procedure. However, you can execute these types of SQL statements against objects in a user-defined relational container schema \(for example, \(SYSHDL\_*<relational\_container\_name\>*\_MYSCHEMA\) as long as you have the applicable data lake Relational Engine privileges on the relational container schema.

For example, the following CREATE TABLE statement returns a permission error because it is trying to create the table in the default relational container schema SYSHDL\_CONTAINER1.

```
CREATE TABLE SYSHDL_CONTAINER1.T3 (COL1 INT, COL2 INT);
```

But the same CREATE TABLE statement works if you specify the user-defined relational container schema MYSCHEMA in relational container SYSHDL\_CONTAINER1.

```
CREATE TABLE SYSHDL_CONTAINER1_MYSCHEMA.T3 (COL1 INT, COL2 INT);
```

